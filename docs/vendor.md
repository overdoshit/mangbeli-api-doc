# **API Documentation - Vendor Information**

---
## **Get My Profile Vendor Information**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/vendor/profile`
- **Method:** `GET`

## Description

> This endpoint is used to retrieve vendor profile information for the authenticated user.

## Request

### Headers

| Key            | Value                                | Required | Description                                |
| -------------- | ------------------------------------ | -------- | ------------------------------------------ |
| `Authorization`| Bearer `<accessToken>`               | Yes      | Authentication token for user authorization|

#### Example
```bash
curl -X GET "https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/vendor/profile" \
-H "Authorization: Bearer <accessToken>"
```

## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
    "error": false,
    "message": "Vendor fetched successfully",
    "dataVendor": {
        "vendorId": "BQX7Slyu8W",
        "userId": "sxSdOtPSeU",
        "name_vendor": "Mie Ayam Dadang",
        "products": "[\"Mie Ayam Pangsit\", \"Mie Ayam Bakso\"]",
        "minPrice": 10000,
        "maxPrice": 25000,
        "createdAt": "2023-12-05T06:29:55.000Z",
        "updatedAt": "2023-12-05T06:29:55.000Z"
    }
}
```

### Error Responses

- **Status Code:** `401 Unauthorized`
    - Missing access token
        ```json
        {
            "error": true,
            "message": "Missing access token"
        }
        ```

- **Status Code:** `403 Forbidden`
    - Invalid access token
        ```json
        {
            "error": true,
            "message": "Invalid access token"
        }
        ```

    - Invalid role
        ```json
        {
            "error": true,
            "message": "Invalid role"
        }
        ```

- **Status Code:** `500 Internal Server Error`
    - Internal server error
        ```json
        {
            "error": true,
            "message": "Internal Server Error",
            "errorMessage": "Details about the internal server error"
        }
        ```


---
## **Update My Profile Vendor Information**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/vendor/profile`
- **Method:** `PATCH`

## Description

> This endpoint is used to update information about a vendor profile, such as name vendor, products, minimum price, and maximum price.

## Request

### Headers

| Key            | Value                                | Required | Description                                |
| -------------- | ------------------------------------ | -------- | ------------------------------------------ |
| `Authorization`| Bearer `<accessToken>`               | Yes      | Authentication token for user authorization|

### Body

| Key             | Type    | Required | Description                      |
| --------------- | ------- | -------- | -------------------------------- |
| `name_vendor`   | string  | Optional | New name of the vendor            |
| `products`      | string  | Optional | Updated product details          |
| `minPrice`      | int     | Optional | New minimum price                |
| `maxPrice`      | int     | Optional | New maximum price                |

#### Example
```bash
curl -X PATCH "https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/update-profile" \
-H "Authorization: Bearer <accessToken>" \
-d '{
    "name_vendor": "Mie Ayam Dadang Makmur",
    "products": "["Mie Ayam Pangsit", "Mie Ayam Bakso", "Mie Yamin"]",
    "minPrice": 11000,
    "maxPrice": 27000
    }'
```

## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
    "error": false,
    "message": "Vendor updated successfully"
}
```

### Error Responses

- **Status Code:** `401 Unauthorized`
    - Missing access token
        ```json
        {
            "error": true,
            "message": "Missing access token"
        }
        ```

- **Status Code:** `403 Forbidden`
    - Invalid access token
        ```json
        {
            "error": true,
            "message": "Invalid access token"
        }
        ```

    - Invalid role
        ```json
        {
            "error": true,
            "message": "Invalid role"
        }
        ```

- **Status Code:** `500 Internal Server Error`
    - Internal server error
        ```json
        {
            "error": true,
            "message": "Internal Server Error",
            "errorMessage": "Details about the internal server error"
        }
        ```


---
## **Get Vendor Information by vendorId**

## URL

**https://mangbeli-auth-1-vb76nyymeq-et.a.run.app**

## Endpoint

- **URL:** `/vendor`
- **Method:** `GET`

## Description

> This endpoint is used to retrieve information about a specific vendor based on their vendorId.

## Request

### Headers

| Key            | Value                                | Required | Description                                |
| -------------- | ------------------------------------ | -------- | ------------------------------------------ |
| `Authorization`| Bearer `<accessToken>`               | Yes      | Authentication token for user authorization|

### Query Parameters

| Key           | Type                                 | Required | Description                               |
| ------------- | ------------------------------------ | -------- | ----------------------------------------- |
| `vendorId`    | string                               | Yes      | Vendor ID to fetch information for        |

#### Example
```bash
curl -X GET "https://mangbeli-auth-1-vb76nyymeq-et.a.run.app/vendor?vendorId=ciz9KF75VR" \
-H "Authorization: Bearer <accessToken>"
```

## Response

### Success Response

- **Status Code:** `200 OK`
```json
{
    "error": false,
    "message": "Vendor fetched successfully",
    "dataVendor": {
        "vendorId": "ciz9KF75VR",
        "userId": "oy4wePSPdI",
        "name_vendor": "Bakso Sri",
        "products": "[\"Bakso Urat\", \"Bakso Telor\", \"Bakso Mercon\"]",
        "minPrice": 12000,
        "maxPrice": 30000,
        "createdAt": "2023-12-05T06:30:30.000Z",
        "updatedAt": "2023-12-05T06:30:30.000Z"
    }
}
```

### Error Responses

- **Status Code:** `400 Bad Request`
    - Invalid input or missing fields
    ```json
    {
        "error": true,
        "message": "Parameter vendorId required"
    }
    ```

- **Status Code:** `401 Unauthorized`
    - Missing access token
        ```json
        {
            "error": true,
            "message": "Missing access token"
        }
        ```

- **Status Code:** `403 Forbidden`
    - Invalid access token
        ```json
        {
            "error": true,
            "message": "Invalid access token"
        }
        ```

- **Status Code:** `404 Not Found`
    - Specified vendorId is not found
        ```json
        {
            "error": true,
            "message": "Vendor not found"
        }
        ```

- **Status Code:** `500 Internal Server Error`
    - Internal server error
        ```json
        {
            "error": true,
            "message": "Internal Server Error",
            "errorMessage": "Details about the internal server error"
        }
        ```

!> Any other HTTP method will result in a **405 Method Not Allowed** response.