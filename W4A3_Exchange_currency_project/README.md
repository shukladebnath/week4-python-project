# W4-A3 Exchange Currency Project – Class Diagram

## 1. Number of Class Diagrams

Based on the defined scope of the **W4-A3 Exchange Currency Project**, **one class diagram** is created.

One class diagram is sufficient because the project focuses on the main business functions of the Money Exchange System. The diagram shows the main classes, their attributes, methods, relationships, and multiplicities in one clear view.

## 2. Purpose of the Class Diagram

The class diagram represents the object-oriented design of the Money Exchange System.

It is based on the project scope and the use cases from the W3-A5 project, including:

- Login
- View Exchange Rates
- View Transactions
- Manage Customers
- Manage Currencies
- Manage Exchange Rates
- Process Exchange Transaction
- Calculate Converted Amount

The diagram shows how the main objects of the system work together to complete a currency exchange.

## 3. Main Classes

### Customer

The **Customer** class represents a customer who uses the money exchange service.

**Main attributes:**
- customer_id
- first_name
- last_name
- phone
- email
- address
- created_at

**Main methods:**
- `__init__()`
- `get_full_name()`
- `update_info()`
- `is_valid()`

### Transaction

The **Transaction** class represents a currency exchange transaction made by a customer.

**Main attributes:**
- transaction_id
- customer_id
- rate_id
- amount_from
- amount_to
- payment_method_id
- transaction_date
- notes

**Main methods:**
- `__init__()`
- `calculate_exchange()`
- `get_details()`

### Currency

The **Currency** class represents a currency supported by the exchange business.

Examples include:

- NZD – New Zealand Dollar
- USD – US Dollar
- AUD – Australian Dollar

**Main attributes:**
- currency_id
- currency_code
- currency_name
- symbol
- is_active

**Main methods:**
- `__init__()`
- `activate()`
- `deactivate()`
- `get_by_code()`

### ExchangeRate

The **ExchangeRate** class stores the exchange rate between two currencies.

For example:

`NZD → USD = 0.60`

**Main attributes:**
- rate_id
- from_currency_id
- to_currency_id
- rate
- rate_date
- is_active

**Main methods:**
- `__init__()`
- `calculate_amount()`
- `deactivate()`

### PaymentMethod

The **PaymentMethod** class represents the method used to pay for an exchange transaction.

The system supports:

- Cash
- Card

**Main attributes:**
- payment_method_id
- method_name
- description
- is_active

**Main methods:**
- `__init__()`
- `activate()`
- `deactivate()`

## 4. Relationships Between Classes

### Customer – Transaction

One customer can make many transactions.

**Relationship:**

`Customer 1 ───── * Transaction`

This means:
- One Customer can have many Transactions.
- Each Transaction belongs to one Customer.

### ExchangeRate – Transaction

One exchange rate can be used by many transactions.

**Relationship:**

`ExchangeRate 1 ───── * Transaction`

This allows the system to use a stored exchange rate when processing currency exchanges.

### Currency – ExchangeRate

An exchange rate requires two currencies:

- `from_currency`
- `to_currency`

For example:

`NZD → USD`

Therefore, the `Currency` class has two separate relationships with `ExchangeRate`.

**Relationships:**

`Currency 1 ───── * ExchangeRate (from_currency)`

`Currency 1 ───── * ExchangeRate (to_currency)`

The same Currency class is used for both the source and destination currency.

### PaymentMethod – Transaction

A payment method can be used for many transactions.

**Relationship:**

`PaymentMethod 1 ───── * Transaction`

The available payment methods are **Cash** and **Card**.

## 5. Functionality Represented

The class diagram represents the following main functionality:

1. **Customer Management**  
   Customer information can be stored and managed.

2. **Currency Management**  
   The system can store supported currencies such as NZD, USD and AUD.

3. **Exchange Rate Management**  
   Exchange rates can be stored between two currencies.

4. **Currency Exchange**  
   A customer can exchange an amount from one currency to another.

5. **Converted Amount Calculation**  
   The `ExchangeRate` and `Transaction` classes support calculating the converted amount.

6. **Payment Processing**  
   A transaction can be paid using Cash or Card.

7. **Transaction Management**  
   Completed exchanges can be recorded and viewed.

## 6. OOP Design

The diagram follows Object-Oriented Programming principles.

Each important business concept is represented as a class. Each class contains:

- **Attributes** – data belonging to the object.
- **Methods** – operations or behaviour performed by the object.

For example, the `Transaction` class contains the exchanged amounts and provides the `calculate_exchange()` method.

## 7. Class Diagram File

The class diagram is provided as:

**`MoneyExchange_ClassDiagram.png`**

## 8. Project Files

The project contains the following main files:

| File | Purpose |
|---|---|
| `database.py` | Creates the SQLite database and tables |
| `models.py` | Defines the OOP classes |
| `data_insertion.py` | Inserts sample data |
| `main.py` | Runs the Money Exchange System |
| `queries.py` | Contains SQL queries |
| `money_exchange.db` | SQLite database |
| `MoneyExchange_ClassDiagram.png` | Class diagram |
| `README.md` | Project and class diagram description |

## 9. Conclusion

The single class diagram provides a clear object-oriented view of the W4-A3 Money Exchange System. It shows the five main business classes—**Customer, Transaction, Currency, ExchangeRate, and PaymentMethod**—and explains how they work together to support customer management, currency exchange, exchange-rate management, transaction processing, and Cash/Card payments.