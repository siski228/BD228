# BD228
Выберите из таблицы orders все заказы

SELECT * FROM orders 

![image](https://github.com/user-attachments/assets/46efc6ca-f163-4f31-9287-5be6a141a4ce)


2) Выберите из таблицы orders все заказы кроме новых. У новых заказов status равен "new". Использовать in

SELECT * FROM orders WHERE STATUS IN ('cancelled','in_progress','delivery')

![image](https://github.com/user-attachments/assets/73c92258-7a54-4388-b66b-5fd97b2017fd)


3) Выберите из таблицы orders все новые и отмененные заказы. У отмененных заказов status равен "cancelled". У новых заказов status равен "new".

SELECT * FROM orders WHERE status IN ('new', 'cancelled');

![image](https://github.com/user-attachments/assets/5fddf410-be1d-4cff-b8ad-6fbfc0d97791)


4) Выберите из таблицы orders все заказы содержащие более 3 товаров (products_count).
Вывести нужно только номер (id) и сумму (sum) заказа.

SELECT id, sum FROM orders WHERE products_count > 3;

![image](https://github.com/user-attachments/assets/10bcca88-bb6c-45b6-9549-c2204f08ec12)


**лабик 2**


1. Выберите из таблицы orders 3 самых дешевых заказа за всё время. Данные нужно отсортировать в порядке убывания цены. Отмененные заказы не учитывайте

![image](https://github.com/user-attachments/assets/32cdb08f-3bcb-48f7-97e3-bb5b98f4da1e)

SELECT * FROM orders WHERE STATUS !='canseled' order by sum ASC LIMIT 3

2. Выберите из таблицы orders 2 самых дорогих заказов за всё время. Данные нужно отсортировать в порядке убывания цены. Отмененные заказы не учитывайте.

![image](https://github.com/user-attachments/assets/2d40d350-0f89-4e0f-a924-7300f7a3ea4e)

SELECT * FROM orders WHERE STATUS !='canseled' order by SUM desc LIMIT 2

3.Добавьте в таблицу orders данные о новом заказе стоимостью 8000 рублей. В заказе 4 товара (products).

![image](https://github.com/user-attachments/assets/408da81e-e7c7-4175-b79b-2f4054a1c523)

INSERT INTO orders (id, products, SUM) VALUES (6,4,8000)

4.Добавьте в таблицу products новый товар — «VR-очки», стоимостью 70000 рублей в количестве (count) 2 штук.

![image](https://github.com/user-attachments/assets/e73be73f-5ba7-41ef-90bf-79e7081eb643)

INSERT INTO products (id,NAME,count,price) VALUES (7,'VR-очки',2,70000)

5) В таблицу products внесли данные с ошибкой, вместо "PS5" в наименовании написали IMAC. Исправьте ошибку.

![image](https://github.com/user-attachments/assets/3d415960-8ad8-4914-a38b-0be22cd122c3)

UPDATE products SET NAME='PS5' WHERE NAME='IMAC'


**лабик 3**

                                    
 Создайте таблицу users с полем id типа INT и двумя текстовыми полями, которые будут хранить имя (first_name) и фамилию (last_name). Длина имени и фамилии не превышает 50 символов.

Добавьте в таблицу трех пользователей: Дмитрия Иванова, Анатолия Белого и Дениса Давыдова.

![image](https://github.com/user-attachments/assets/8c40f261-e61a-438a-a779-ad3c5e21e3ea)

CREATE TABLE USERS (
    id INT,
    first_name VARCHAR(50),
    last_name VARCHAR(50)
);
INSERT INTO USERS (id,first_name,last_name) VALUES
(1, 'Дмитрий', 'Иванов'),
(2, 'Анатолий', 'Белый'),
(3, 'Денис','Давыдов');


**лабик 4**

                                    
1.Создайте таблицу users для хранения информации о пользователях сайта. В таблице должны быть следующие поля: id – идентификатор, целое положительное; email – адрес электронной почты, строка не более 100 символов; date_joined – дата регистрации (достаточно хранить дату, без времени) last_activity – дата и время последней активности (с точностью до секунд).

![image](https://github.com/user-attachments/assets/b53b39ec-6dfe-4c74-a196-6f27473d9213)


Неверное решение:

CREATE TABLE users(id INT UNSIGNED, email VARCHAR(100), date_joined DATE, last_activity DATETIME); INSERT INTO users (id, email, date_joined, last_activity) VALUES (1, "user1@domain.com", "2014-12-12", "2016-04-08 12:34:54") INSERT INTO users (id, email, date_joined, last_activity) VALUES (2, "user2@domain.com", "2014-12-12", "2017-02-13 11:46:53") INSERT INTO users (id, email, date_joined, last_activity) VALUES (3, "user3@domain.com", "2014-12-13", "2017-04-04 05:12:07")

Верное решение:

create table users ( id int(10) unsigned, email varchar (100), date_joined date, last_activity datetime );
insert into users (id, email, date_joined,last_activity) values (1,'user1@domain.com', '2014-12-12','2016-04-08 12:34:54'),
(2,'user2@domain.com', '2014-12-12','2017-02-13 11:46:53'), (3,'user3@domain.com', '2014-12-13','2017-04-04 05:12:07');

![image](https://github.com/user-attachments/assets/02a3bbd8-d8c0-4ab0-a7b3-799eb965f876)

2.Создайте таблицу calendar для хранения календаря посетителей. В таблице должны быть следующие поля: id – идентификатор записи в календаре, целое положительное; user_id – идентификатор пользователя, целое положительное; doctor_id – идентификатор доктора, целое положительное; visit_date – дата и время визита (точность до секунд).

![image](https://github.com/user-attachments/assets/3fb2e305-bcf6-4f4b-b078-845131f06097)

Неверное решение:

Create table calendar ( id int unsigned, user_id int unsigned, doctor_id int unsigned, visit_date datetime); Insert into calendar (id, user_id, doctor_id, visit_date) Values (1, 1914 , 1, '2017-04-08 12:00:00'), (2, 12, 1, '2017-04-08 12:30:00'), (3, 4641, 2, '2017-04-09 09:00:00'), (4, 4641, 2,'2017-04-09 09:00:00'), (5, 15, 2,'2017-04-09 10:00:00')

Верное решение:

Create table calendar ( id int unsigned, user_id int unsigned, doctor_id int unsigned, visit_date datetime);
Insert into calendar (id, user_id, doctor_id, visit_date) Values (1, 1914 , 1, '2017-04-08 12:00:00'),
(2, 12, 1, '2017-04-08 12:30:00'),(3, 4641, 2, '2017-04-09 09:00:00'),
(4, 784, 1,'2017-04-08 13:00:00'), (5, 15, 2,'2017-04-09 10:00:00') 

![image](https://github.com/user-attachments/assets/45590bce-27be-41b2-b90c-31d45f85f257)

3.Создайте таблицу users , в которой будут следующие поля: id — идентификатор, целые положительные числа. first_name— имя, строки до 50 символов. last_name — фамилия, строки до 60 символов. bio — биография, текст до 65000 символов.

![image](https://github.com/user-attachments/assets/3f71835a-f4f9-432e-8dbd-d475e964be8f)

Неверное решение:

create table users ( id int (10) unsigned, first_name varchar (50) unsigned, last_name varchar (60) unsigned, bio text ); INSERT INTO users (id, first_name, last_name, bio) VALUES (1,'Антон','Кулик','С отличием окончил 39 лицей.'), (2,'Сергей','Давыдов',''), (3,'Дмитрий','Соколов','Профессиональный программист.')

Верное решение:

create table users ( id int (10) unsigned, first_name varchar (50), last_name varchar (60), bio text );
INSERT INTO users (id, first_name, last_name, bio) VALUES (1,'Антон','Кулик','С отличием окончил 39 лицей.'),
(2,'Сергей','Давыдов',''), (3,'Дмитрий','Соколов','Профессиональный программист.')

![image](https://github.com/user-attachments/assets/7c95946a-9c5b-4389-90f1-6aeab751a99b)


**лабик 5**


1.Выберите из таблицы orders 4 самых дорогих заказов за всё время.Данные нужно отсортировать в порядке убывания цены.Отмененные заказы не учитывайте.

![image](https://github.com/user-attachments/assets/a457909f-6a32-4d28-9e9d-c8c87ecd4258)

SELECT * FROM orders WHERE status != 'cancelled' ORDER BY sum DESC LIMIT 4;

![image](https://github.com/user-attachments/assets/7aeae81c-fc48-40ae-98bb-28e3ad7d15ba)

2.Выберите из таблицы products название и цены четырех самых дешевых товаров, которые есть на складе.

![image](https://github.com/user-attachments/assets/48dedbf1-6c22-4cf8-985d-ba411e5921fd)

SELECT name, price FROM products WHERE count > 0 ORDER BY price ASC LIMIT 4;

![image](https://github.com/user-attachments/assets/cc99aec8-4d68-41e2-b473-a598c2e63a87)

3.Выберите из таблицы orders три последних заказа (по дате date) стоимостью от 3200 рублей и выше. Данные отсортируйте по дате в обратном порядке.

![image](https://github.com/user-attachments/assets/0393afc9-2b01-4c05-980e-b24f84fc02b3)

SELECT * FROM orders WHERE sum >= 3200 ORDER BY date DESC LIMIT 3;

![image](https://github.com/user-attachments/assets/c07833fa-5cec-43af-a02c-f66b1e068d6e)

4.Создайте данную таблицу:

![image](https://github.com/user-attachments/assets/bc32d10f-e836-417e-907b-5795b2bd0189)

CREATE TABLE products (
    id INT PRIMARY KEY,
    name VARCHAR(255),
    count INT,
    price DECIMAL(10, 2)
);

INSERT INTO products (id, name, count, price) VALUES
(1, 'Стиральная машина', 5, 10000),
(2, 'Холодильник', 0, 10000),
(3, 'Микроволновка', 3, 4000),
(4, 'Пылесос', 2, 4500),
(5, 'Вентилятор', 0, 700),
(6, 'Телевизор', 7, 31740),
(7, 'Тостер', 2, 2500),
(8, 'Принтер', 4, 3000),
(9, 'Активные колонки', 1, 2900),
(10, 'Ноутбук', 4, 36990),
(11, 'Посудомоечная машина', 0, 17800),
(12, 'Видеорегистратор', 23, 4000),
(13, 'Смартфон', 8, 12300.),
(14, 'Флешка', 4, 1400),
(15, 'Блендер', 0, 5500),
(16, 'Газовая плита', 5, 11900),
(17, 'Клавиатура', 3, 1800);

![image](https://github.com/user-attachments/assets/abe397a7-a836-4b1a-9f8b-ea5bb45780c3)

5.Из таблицы ниже сделать выборку на основе задания: Сайт выводит товары по 5 штук. Выберите из таблицы products товары, которые пользователи увидят на 3 странице каталога при сортировке в порядке возрастания цены (price).

![image](https://github.com/user-attachments/assets/6f4ff6e1-7581-4428-ae94-5dfb904b1895)

SELECT name, price FROM products ORDER BY price ASC LIMIT 5 OFFSET 10;

![image](https://github.com/user-attachments/assets/4088185e-b7af-4c53-bc12-23216534da92)


**лабик 6**


1.Создайте таблицу orders для хранения списка заказов: id — идентификатор, целое положительное. user_id — идентификатор пользователя, который оформил заказ. Целое положительное, NULL запрещен. amount — стоимость заказа. Целое положительное число не более 1 млн. NULL запрещен, по умолчанию 0. created — дата и время создания заказа. NULL запрещен. state — статус заказа. Выбор из new, cancelled, in_progress, delivered, completed. Можно выбрать только один вариант. NULL запрещен. По умолчанию должен стоять new. Добавьте 3 записи так, чтобы получалась таблица ниже:

![image](https://github.com/user-attachments/assets/9f278151-3dfa-4bff-98c5-45785eb3cf32)

CREATE TABLE orders (
    id INTEGER PRIMARY KEY AUTO_INCREMENT,
    user_id INTEGER NOT NULL,
    amount INTEGER NOT NULL DEFAULT 0,
    created DATETIME NOT NULL,
    state ENUM('new', 'cancelled', 'in_progress', 'delivered', 'completed') NOT NULL DEFAULT 'new',
    CHECK (user_id > 0),
    CHECK (amount >= 0 AND amount <= 1000000)
);

INSERT INTO orders (user_id, amount, created) VALUES (56, 5400, '2018-02-01 17:46:59');
INSERT INTO orders (user_id, amount, created) VALUES (90, 249, '2018-02-01 19:13:04');
INSERT INTO orders (user_id, amount, created) VALUES (78, 2200, '2018-02-01 22:43:09');

SELECT * FROM orders;

![image](https://github.com/user-attachments/assets/ca409fae-a747-47ee-a689-215493daf8f9)

2.Создайте таблицу users для хранения списка пользователей сайта: id — идентификатор, целое положительное. first_name — имя, строка до 20 символов. NULL запрещен. last_name — фамилия, строка до 20 символов. NULL запрещен. patronymic — отчество, строка до 20 символов. NULL запрещен, по умолчанию пустая строка. is_active — отметка об активности пользователя. Логическое поле, по умолчанию TRUE. is_superuser — отметка администратора. Логическое поле, по умолчанию FALSE. Добавьте 3 записи так, чтобы получалась таблица

![image](https://github.com/user-attachments/assets/50cd288b-7581-49dc-be74-f6f4d098de42)

CREATE TABLE users (
    id INTEGER PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(20) NOT NULL,
    last_name VARCHAR(20) NOT NULL,
    patronymic VARCHAR(20) NOT NULL DEFAULT '',
    is_active BOOLEAN NOT NULL DEFAULT TRUE,
    is_superuser BOOLEAN NOT NULL DEFAULT FALSE,
    CHECK (LENGTH(first_name) <= 20),
    CHECK (LENGTH(last_name) <= 20),
    CHECK (LENGTH(patronymic) <= 20)
);

INSERT INTO users (first_name, last_name, patronymic, is_active, is_superuser)
VALUES ('Дмитрий', 'Иванов', '', TRUE, FALSE);

INSERT INTO users (first_name, last_name, patronymic, is_active, is_superuser)
VALUES ('Анатолий', 'Белый', 'Сергеевич', TRUE, TRUE);

INSERT INTO users (first_name, last_name, is_active, is_superuser)
VALUES ('Андрей', 'Крючков', FALSE, FALSE);

SELECT * FROM users;

![image](https://github.com/user-attachments/assets/474dba56-5a9d-47ec-9bae-1ceac68d8bdb)

3.Создайте таблицу products для хранения товаров в интернет магазине: id — идентификатор, целое положительное. category_id — категория, целое положительное. Может принимать NULL. По умолчанию NULL. name — название, строка до 100 символов. NULL запрещен. count — количество, целое положительное до 255. NULL запрещен, по умолчанию 0. price — цена типа DECIMAL с 10 знаками, 2 из которых выделены для копеек. NULL запрещен, по умолчанию 0.00. Добавьте 3 записи так, чтобы получалась таблица

CREATE TABLE products (
    id INTEGER PRIMARY KEY AUTO_INCREMENT,
    category_id INTEGER NULL DEFAULT NULL,
    name VARCHAR(100) NOT NULL,
    count TINYINT UNSIGNED NOT NULL DEFAULT 0,
    price DECIMAL(10, 2) NOT NULL DEFAULT 0.00,
    CHECK (category_id > 0 OR category_id IS NULL),
    CHECK (count >= 0 AND count <= 255),
    CHECK (price >= 0)
);

INSERT INTO products (category_id, name, count, price)
VALUES (1, 'Кружка', 5, 45.90);

INSERT INTO products (category_id, name, count, price)
VALUES (17, 'Фломастеры', 0, 78.00);

INSERT INTO products (name, count, price)
VALUES ('Сникерс', 12, 50.80);

SELECT * FROM products;

![image](https://github.com/user-attachments/assets/cdb7cacc-b54f-4161-a5d7-cf17046f4300)
