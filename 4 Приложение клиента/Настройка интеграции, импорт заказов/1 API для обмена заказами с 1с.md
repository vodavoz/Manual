---
order: 703
date: 2025-07-16
---

# API для обмена заказами с 1с
Прием заказов организован через работу http сервисов, идет общение между сервисами в формате json. При обращении указывается адрес для обращения, порт и имя публикации, далее следует стандартный метод обращения [!badge variant="light" text="[/hs/AquaDeliveri/getOrdersURL]"]  Как пример итоговой адресной строки строки http://92.241.102.242:8888/demodelivery/hs/AquaDeliveri/getOrdersURL


## Параметры
В качестве параметров запроса передается массив заказов, которые необходимо создать/обновить в текущей системе [!badge variant="light" text="[order, order...]"] . Ниже пример запроса с расшифровкой параметров


==-** Пример

```json

[
    {
        "id": "657f9553-ff97-11e9-80d3-001e4f377cd7",
        "external_id": null,
        "payment_type": "cash",
        "comment": "comment",
        "shipping_date_from": "2019-11-06T11:00:00Z",
        "shipping_date_to": "2019-11-06T18:00:00Z",
        "status": "new",
        "total": 710,
        "delivery_cost": 30,
        "coins": 710,
        "order_item_list": [
            {
                "name": "Вода 19 л. Ваш бренд",
                "id": "78e66cef-ae2c-11e6-9bf1-f8a9634f667f",
                "external_id": 1,
                "product_id": "78e66cef-ae2c-11e6-9bf1-f8a9634f667f",
                "price": 355,
                "quantity": 2,
                "order_product_id": 1435
            }
        ],
        "shipping_address": {
            "city": "Сыктывкар",
            "street": "Кутузова",
            "house": "19",
            "entrance": null,
            "floor": null,
            "room": null,
            "str": "город Сыктывкар улица Кутузова дом 19"
        },
        "client": {
            "id": "jqLbQR3be8jlJZIh4dBrUCyyIhFzuAKK",
            "external_id": 68,
            "account_number": 68,
            "type": "fiz",
            "username": "Василий Тестовый",
            "addresses": [
                {
                    "id": "78e66cef-ae2c-11e6-9bf1-f8a9634f667f",
                    "external_id": null,
                    "city": "Сыктывкар",
                    "street": "Кутузова",
                    "house": "19",
                    "entrance": null,
                    "floor": null,
                    "room": null,
                    "str": "город Сыктывкар улица Кутузова дом 19"
                }
            ]
        }
    }
]

```
==-
==-** Ответ

```json

{
    "success": true,
    "data": {
        "657f9553-ff97-11e9-80d3-001e4f377cd7": {
            "success": true,
            "data": [
                {
                    "id": "50894",
                    "external_id": "657f9553-ff97-11e9-80d3-001e4f377cd7",
                    "status": "approved",
                    "client": {
                        "id": 68,
                        "external_id": "jqLbQR3be8jlJZIh4dBrUCyyIhFzuAKK",
                        "username": "Василий Тестовый",
                        "comment": null,
                        "email": "ognev@baitek.org",
                        "account_number": 68,
                        "type": "fiz",
                        "phones": [
                            "9083280832"
                        ],
                        "addresses": [
                            {
                                "id": 2647,
                                "external_id": null,
                                "name": "Кутузова, д. 21, эт. 1, кв./оф. 1, под. 2, г. Сыктывкар – Орбита ближняя (Париж)",
                                "city": "Сыктывкар",
                                "street": "Кутузова",
                                "house": "21",
                                "room": "1",
                                "entrance": "2",
                                "floor": "1",
                                "district_id": 1,
                                "str": "Кутузова, д. 21, эт. 1, кв./оф. 1, под. 2, г. Сыктывкар   Орбита ближняя (Париж)"
                            }
                        ],
                        "requisites": {
                            "bank_account": {
                                "inn": "1234512345",
                                "kpp": "1234512345",
                                "account_number": "1234512345",
                                "correspondent_account": "1234512345",
                                "bik": "1234512345",
                                "bank_name": "1234512345"
                            }
                        },
                        "legal_address": [
                            "г. Сыктывкар,ул. Кутузова,д. 21"
                        ],
                        "product_price_list": {
                            "36": {
                                "product_id": 36,
                                "external_product_id": null,
                                "price": "101.00",
                                "active": false
                            }
                        },
                        "coins_amount": 90,
                        "loyalty_system_is_active": true
                    },
                    "account_number": 68,
                    "total": 710,
                    "delivery_cost": 30,
                    "coins": 710,
                    "payment_type": "cash",
                    "created_at": "2019-11-07 00:54:05",
                    "shipping_address": null,
                    "shipping_date_from": "2019-11-06 14:00:00",
                    "shipping_date_to": "2019-11-06 21:00:00",
                    "order_item_list": [
                        {
                            "name": "Вода 19 л. Ваш бренд",
                            "quantity": 2,
                            "price": 355,
                            "product_id": 28,
                            "order_product_id": 1435
                        }
                    ],
                    "comment": "comment",
                    "ask_for_checkout": null,
                    "count_of_returned_bottles": 0
                }
            ]
        }
    }
}
```
==-

<table>
  <thead>
    <tr>
      <th>Название</th>
      <th>Тип  2</th>
      <th>Обязательный 3</th>
      <th>Описание 3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>id</td>
      <td>string(255</td>
      <td>true</td>
      <td>Идентификатор в экспортирующей системе (внешнее приложение или сайт)</td>
    </tr>
    <tr>
      <td>external_id</td>
      <td>integer(11)</td>
      <td>false</td>
      <td>Идентификатор в принимающей системе (1с)</td>
    </tr>
  </tbody>
   <tr>
      <td>status</td>
      <td>range in 'new', 
      'approved', 
      'completed', 
      'removed'</td>
      <td>true</td>
      <td>Статус заказа
new - новый неразобранный заказ
approved - назначен курьер для доставки (заказ обработан оператором)
completed - доставлено
removed - отменено (диспетчером или клиентом)</td>
    </tr>
  </tbody>
   <tr>
      <td>created_at</td>
      <td>datetime</td>
      <td>false</td>
      <td>Дата создания</td>
    </tr>
  </tbody>
  </tr>
      <td>total</td>
      <td>float</td>
      <td>true</td>
      <td>Сумма заказа (стоимость 
      доставки включена)</td>
  <tr>
      <td>delivery_cost</td>
      <td>float</td>
      <td>false</td>
      <td>Стоимость доставки</td>
    </tr>
  </tbody>
  <tr>
      <td>coins</td>
      <td>float</td>
      <td>false</td>
      <td>Кол-во баллов, которые использовались 
      для оплаты заказа</td>
    </tr>
  </tbody>
  <tr>
      <td>payment_type</td>
      <td>range</td>
      <td>false</td>
      <td>Способ оплаты (указывается строкой, соответствие настраивается в соответствующем разделе настроек) </td>
    </tr>
  </tbody>
  <tr>
      <td>shipping_date_from</td>
      <td>datetime</td>
      <td>true</td>
      <td>Время доставки от</td>
    </tr>
  </tbody>
  <tr>
      <td>shipping_date_to</td>
      <td>datetime</td>
      <td>true</td>
      <td>Время доставки до</td>
    </tr>
  </tbody>
  <tr>
      <td>comment</td>
      <td>string</td>
      <td>false</td>
      <td>Комментарий</td>
    </tr>
  </tbody>
  <tr>
      <td>count_of_returned_bottles</td>
      <td>integer</td>
      <td>false</td>
      <td>Кол-во бутылей 
      к возврату</td>
    </tr>
  </tbody>
  <tr>
      <td>order_item_list</td>
      <td>array</td>
      <td>true</td>
      <td>Массив из заказанных позиций</td>
    </tr>
  </tbody>
  <tr>
      <td>client</td>
      <td>object</td>
      <td>true</td>
      <td>Объект содержащий клиента</td>
    </tr>
  </tbody>
  <tr>
      <td>shipping_address</td>
      <td>object</td>
      <td>true</td>
      <td>Объект содержащий адрес доставки</td>
    </tr>
  </tbody>
</table>




Атрибуты объекта клиент [!badge variant="light" text="client"], если он существует в системе можно посмотреть здесь

Атрибуты объекта клиент [!badge variant="light" text="client"], если заказ от не зарегистрированного пользователя




<table>
  <thead>
    <tr>
      <th>Название</th>
      <th>Тип  2</th>
      <th>Обязательный 3</th>
      <th>Описание 3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>username</td>
      <td>string(255</td>
      <td>true</td>
      <td>Имя клиента</td>
    </tr>
    <tr>
      <td>phone</td>
      <td>string(12)(11)</td>
      <td>true</td>
      <td>Телефон клиента, например +79191991919</td>
    </tr>
  </tbody>
   <tr>
      <td>emai</td>
      <td>string(255)</td>
      <td>false</td>
      <td>Электронная почта клиента</td>
    </tr>
  </tbody>
 </table>

 

Атрибуты объекта адрес доставки [!badge variant="light" text="shipping_address"]  




<table>
  <thead>
    <tr>
      <th>Название</th>
      <th>Тип  2</th>
      <th>Обязательный 3</th>
      <th>Описание 3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>user_address_id</td>
      <td>integer(11)</td>
      <td>false</td>
      <td>Идентификатор в принимающей системе</td>
    </tr>
    <tr>
      <td>city</td>
      <td>string(255)</td>
      <td>true</td>
      <td>Город</td>
    </tr>
  </tbody>  
  <tr>
      <td>street</td>
      <td>string(255)</td>
      <td>true</td>
      <td>Улица</td>
    </tr>
  </tbody>
  <tr>
      <td>house</td>
      <td>string(10)</td>
      <td>true</td>
      <td>Дом</td>
    </tr>
  </tbody>
  <tr>
      <td>entrance</td>
      <td>string(10)</td>
      <td>false</td>
      <td>Подъезд</td>
    </tr>
  </tbody>
  <tr>
      <td>floor</td>
      <td>string(10)</td>
      <td>false</td>
      <td>Этаж</td>
    </tr>
  </tbody>
  <tr>
      <td>room</td>
      <td>string(10)</td>
      <td>false</td>
      <td>Номер квартиры или офиса</td>
    </tr>
  </tbody>
  <tr>
      <td>str</td>
      <td>string(255)</td>
      <td>true</td>
      <td>Адрес не структурировано, а единой строкой</td>
    </tr>
  </tbody>
 </table>

 

Массив из заказанных позиций [!badge variant="light" text="order_item_list"]  включает в себя заказанные позиции [!badge variant="light" text="[order_item, order_item...]"]  со следующими атрибутами




<table>
  <thead>
    <tr>
      <th>Название</th>
      <th>Тип  2</th>
      <th>Обязательный 3</th>
      <th>Описание 3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>product_id</td>
      <td>string(255)</td>
      <td>true</td>
      <td>Идентификатор продукта в экспортирующей системе (внешнее приложение, сайт)</td>
    </tr>
    <tr>
      <td>price</td>
      <td>decimal(10,2)</td>
      <td>true</td>
      <td>Цена продукта</td>
    </tr>
  </tbody>  
  <tr>
      <td>quantity</td>
      <td>integer(11)</td>
      <td>true</td>
      <td>Кол-во заказанных продуктов</td>
    </tr>
  </tbody>
  <tr>
      <td>id</td>
      <td>string(255)</td>
      <td>false</td>
      <td>Идентификатор позиции заказа в 1с</td>
    </tr>
  </tbody>
  <tr>
      <td>name</td>
      <td>string(255)</td>
      <td>false</td>
      <td>Название продукта</td>
    </tr>
  </tbody>
 </table>


 

## Ключевые моменты

- [x] Если не будет найден продукт в нашей системе по [!badge variant="light" text="items.id"], то в заказ будет добавлена пустая строка.

- [x] Так же если не будет заполнено какое-то из [!badge variant="light" text="required"]  полей, то данный заказ или пользователь будет проигнорирован для импорта, а в ответ вернётся сообщение об ошибке.

- [x] [!badge variant="light" text="id"] - идентификатор отправляющей системы, [!badge variant="light" text="external_id"]  - идентификатор внешней системы.

- [x] Если внешний идентификатор [!badge variant="light" text="external_id"] ещё не сохранён, то атрибут можно не выводить или оставлять пустым. 
Но после импорта его обязательно необходимо сохранять и выгружать для избежания дублирования.





     
    
