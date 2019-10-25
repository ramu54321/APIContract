# Revenue - Alexa Integration

**Introduction**
---
Api contract for providing overview details for revenue management for various clients. These apis will be used for Alexa integration as well.

**#Revenue**
* Financial Year object
```
{
  id: String
  financial_year: String
  client: String 
  total_revenue: {
    amount: Float(2)
    unit: String (Billion, Million)
    currency: String (INR, USD)
  }
  utilization: {
    value: Integer
    measure: String (Percentage)
  }
  created_at: datetime(iso 8601)
  updated_at: datetime(iso 8601)
}
``` 
**GET /revenue**
----
  Returns all users in the system.
* **URL Params**  
  None
* **Data Params**  
  None
* **Headers**  
  Content-Type: application/json  
  Authorization: Bearer `<OAuth Token>`
* **Success Response:**  
* **Code:** 200  
  **Content:**  
```
{
  revenue: [
           {<financial_year_object>},
           {<financial_year_object>},
           {<financial_year_object>}
         ]
}
```
* **Error Response:**  
  * **Code:** 404  
  **Content:** `{ error : "data not found" }`  
  OR  
  * **Code:** 401  
  **Content:** `{ error : error : "You are unauthorized to make this request." }`

**GET /revenue/:id**
----
  Returns the specified financial year details.
* **URL Params**  
  *Required:* `id=[String]`
* **Data Params**  
  None
* **Headers**  
  Content-Type: application/json  
  Authorization: Bearer `<OAuth Token>`
* **Success Response:** 
* **Code:** 200  
  **Content:**  `{ <financial_year_object> }` 
```
{
  id: "5da01f11ca5f9105bdb7a491",
  financial_year: "2019",
  client: "All Clients",
  total_revenue: {
    amount: 1.57,
    unit: "Billion",
    currency: "USD"
  },
  utilization: {
    value: 83,
    measure: "Percentage"
  },
  created_at: "2019-10-25T10:30:04+0000",
  updated_at: "2019-10-25T10:30:04+0000"
}
```
* **Error Response:**  
  * **Code:** 404  
  **Content:** `{ error : "data doesn't exist" }`  
  OR  
  * **Code:** 401  
  **Content:** `{ error : error : "You are unauthorized to make this request." }`

