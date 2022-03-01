# API CRUD FOR SALES APP

_Using DRF, JWT Auth, Django, Postgres_

## Tables of content

1. [Setup](#set-up)
1. [Models](#create-models)
1. [Add authen](#add-authentication)
1. [API: GET, POST](#api-get-post)
1. [API: DELETE, PUT](#api-delete-put)
1. [Unit-Testing](#unit-testing)
1. [Front-end](#front-end)

## Setup

-   Enviroment
    ```bash
    pip install virtualenv
    virtualenv <yourfolder>
    cd <yourfolder>
    scripts\activate
    git clone https://github/tangoc2712/apicrud
    pip install -r requirements.txt
    ```
-   Project
    ```bash
    python manage.py migrate
    python manage.py makemigrations
    python createsuperuser
    ```

## [Create Models](crud/models.py)

Define model name Order, we're working with one simple table include some fields:

-   date (date)
-   item (char)
-   price (decimal)
-   quantity (decimal)
-   amount (decimal)

## Add authentication

_We using Simple-JWT for auth_

-   First, add config to REST_FRAMEWORK in [settings.py](sales/settings.py#L80)
-   Next in your root [urls.py](sales/urls.py) file (or any other url config), include routes for Simple JWT’s TokenObtainPairView and TokenRefreshView views

To verify it's working, we can use curl or hit on http://127.0.0.1:8000/api/token/ to issue a couple of test requests (username and password from your superuser):

```bash
curl \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"username": "admin", "password": "1"}' \
  http://127.0.0.1:8000/api/token/
```

You'll recieve

```bash
HTTP 200 OK
Allow: POST, OPTIONS
Content-Type: application/json
Vary: Accept
{
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTY0NjI1MzYxOCwianRpIjoiYjMzMDM2ZmVkY2ZhNDQ2ZmIzNjc1ZGEzZTgyZjY0MjUiLCJ1c2VyX2lkIjoxfQ.TM5Z0rPG0Zq33T4iY7euJwovF7TGxwHxRNNqU5h9duo",
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjQ2NzcyMDE4LCJqdGkiOiIyNWE1Zjk1NzQwYTQ0NmY1YTdjMTU0YjczM2M2NDhlNCIsInVzZXJfaWQiOjF9.E8JXvDD9gh7VZMSXfGbBsBm8lI-8Hw8n38aF9LGB_ro"
}
```

## API: GET, POST

## API: DELETE, PUT

## Unit-testing

## Front-end

## License

[MIT]()
