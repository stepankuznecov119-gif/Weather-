# Weather 
import requests

API_KEY = 'bc86ceb1adcf0d727a54f89fa7ce48cd'  

BASE_URL = "http://api.openweathermap.org/data/2.5/weather?"

def get_weather(city):
    complete_url = f"{BASE_URL}appid={API_KEY}&q={city}"
    response = requests.get(complete_url)
    return response.json()

def display_weather_data(weather_data):
    if weather_data['cod'] != 200:
        print("Город не найден или произошла ошибка.")
        return
    main_data = weather_data['main']
    temperature = main_data['temp'] - 273.15  # преобразование в Цельсий
    humidity = main_data['humidity']
    weather_description = weather_data['weather']['description']
    print(f"Температура в {city}: {temperature:.2f}°C, влажность: {humidity}%")
    print(f"Описание погоды: {weather_description}") 

def main():
    city = input("Введите название города: ")
    weather_data = get_weather(city)
    display_weather_data(weather_data)

if __name__ == "__main__":
    main()
