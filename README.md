from random import randint
from time import sleep

igrog = {
    'name': '',
    'armor': 0.95,
    'hp': 100,
    'attack': 5,
    'luck': 10,
    'money': 10000,
    'inventory': []
}

enemies = [
    { 
        'name': 'мелстрой',
        'hp': 10,
        'attack': 10,
        'sctipts': 'ДАВАЙ ДАВАЙ НАПАДАЙ!',
        'win': 'я проиграл, но я ещё вернусь за реваншем',
        'loss': 'ты жалок, иди и не возвращайся'
    },   
    {
        'name': 'райан гослинг',
        'hp': 100,
        'attack': 35,
        'sctipts': '"агрессивное молчание"',
        'win': '"молчание проигравшего"',
        'loss': '"молчание победителя"'
    }, 
    {
        'name': 'стена плоти',
        'hp': 175,
        'attack': 100,
        'sctipts': 'ААААР',
        'win': 'I always come back',
        'loss': 'хи хи хи ха'
    }
]

name= input('введи своё имя')
igrog['name']= name
current_ememy=0

while True:
    action = input('''Выбери действие:
1 - В бой
2 - тренировка
''')
    if action == '1':
            round = randint(1,2)
            ememe=enemies[current_ememy]
            ememe_hp=enemies[current_ememy]['hp']
            print(f'противник - {ememe["name"]} : {ememe["sctipts"]}')
            input('напишите "далие" чтобы продолжить')
            print()
            while igrog['hp'] > 0 and ememe_hp > 0:
             if round % 2==1:
              print(f'{igrog["name"]} атакует {ememe["name"]}.')
              crit= randint(1,50)
              if crit < igrog ['luck']:
                ememe_hp -= igrog['attack'] * 3
              else:
               ememe_hp -= igrog['attack']
             sleep(1)
            else:
             print(f'{ememe["name"]} атакует {igrog["name"]}')
             igrog['hp'] -= ememe['attack'] * igrog['armor']
             sleep(1)
             print(f'''{igrog['name']:{igrog['hp']}}
{ememe['name']}: {ememe_hp}''')
            print()
            sleep(1)
            round += 1

            if igrog['hp'] > 0: 
              print(f'противник- {ememe["name"]} : {ememe["win"]}')
              current_ememy += 1
            else:
             print(f' {ememe["name"]} : {ememe["loss"]}')
            igrog['hp'] = 100
            print()
            

    elif action == '2':
        traning_typ=input('''1 - тренировать атаку
2 - тренировать оборону
''')
        for i in range(0, 101, 20):
            print(f'треня завершина на {i}%')
            sleep(2)
        if traning_typ ==1:
            igrog['attack'] += 2
            print(f'треня окончена велечина отаки повинин до {igrog["attack"]}')
        elif traning_typ == 2:
            igrog['armor'] -= .09
            print(f'треня окончена защита повышина до {100-igrog["armor"] * 100}% урона')
        print()
