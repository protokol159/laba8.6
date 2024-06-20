# laba8.6
Лабораторная работа №8.6. Python вместо браузера

Практическое задание
Задача 1.
Запросите погодный сервис http://wttr.in по URL без параметров. А их задайте словарём weather_parameters. Функция get() должна принимать его, как отдельный аргумент params.

import requests


url = 'https://wttr.in'  # не изменяйте значение URL

weather_parameters = {
    '0': '',
    # добавьте параметр запроса `T`, чтобы вернулся чёрно-белый текст
}

response = ...  # передайте параметры в http-запрос

print(response.text)
Задача 2.
Добавьте в словарь с параметрами weather_parameters ещё два параметра:

M без значения — чтобы скорость ветра была в метрах в секунду, как принято у метеорологов;
lang со значением ru, чтобы прогноз выдавался на русском языке.
Обратите внимание на изменения при добавлении этих параметров.

import requests


url = 'https://wttr.in'  # не изменяйте значение URL

weather_parameters = {
    '0': '',
    'T':''
    # добавьте параметр запроса `T`, чтобы вернулся чёрно-белый текст
}

response = requests.get(url, params=weather_parameters)  # передайте параметры в http-запрос

print(response.text)
Задача 3.
На прошлом уроке вы заказывали страницу на русском языке через параметры в URL.

Сейчас сделайте то же самое, только русский язык запрашивайте через заголовок запроса ‘Accept-Language’.

import requests

url = 'https://wttr.in'

weather_parameters = {
    '0': '',
    'T': '',
    'lang': 'ru',  # удалите этот параметр
    'M': '',
}

request_headers = {
    # заполните словарь с заголовками
}

# не забудьте передать параметры и заголовки в http-запрос
# через аргументы `params` и `headers` функции get()
response = ...
print(response.text)
Задача 4.
Напишите функцию what_weather(), которую затем будете использовать в коде Анфисы:

Выполните HTTP-запрос, поместив вызов функции get() внутрь блока try.
Значения URL и параметров получите из функций make_url() (в неё нужно передать нужный город как аргумент city) и make_parameters().
При «выбрасывании» исключения типа requests.ConnectionError — функция what_weather() должна возвращать сообщение об ошибке '<сетевая ошибка>'.
Если код HTTP-ответа равен 200 (всё хорошо), верните из функции текст ответа. В противном случае функция должна вернуть строку '<ошибка на сервере погоды>'.
import requests


cities = [
    'Омск',
    'Калининград',
    'Челябинск',
    'Владивосток',
    'Красноярск',
    'Москва',
    'Екатеринбург'
]


def make_url(city):
    # в URL задаём город, в котором узнаем погоду
    return f'http://wttr.in/{city}'


def make_parameters():
    params = {
        'format': 2,  # погода одной строкой
        'M': ''  # скорость ветра в "м/с"
    }
    return params


def what_weather(city):
    # Напишите тело этой функции.
    # Не изменяйте остальной код!

print('Погода в городах:')
for city in cities:
    print(city, what_weather(city))
