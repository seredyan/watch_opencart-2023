Homework for online course Python QA Engineer from OTUS
https://otus.ru/lessons/avtomatizaciya-web-testirovaniya/

### Parser for `access.log` file. How-to:
## 1. PAGE OBJECTS:
### Preparation
To run tests for **opencart**:
1. Add `auth.py` in the `pages` directory with the following content structure:

```
class Users:
    ADMIN = {"username": "", "password": ""}
    ADMIN_USER2 = {"username": "", "password": ""}  # need to create
    NON_ADMIN = {"username": "", "password": ""}  # need to create
    NON_EXISTING_USER = {"username": "foofoo", "password": "barbar"}
```

2. Fill in credentials in this file, where:
   1. `ADMIN` is a default '**opencart**' admin (get
      from: https://gist.github.com/konflic/ecd93a4bf7666d97d62bcecbe2713e55)
   2. `ADMIN_USER2` and `NON_ADMIN` do not exist by default. You need to create them manually
      in `http://OPENCART_BASE_URL/admin` (with admin and non-admin rights respectively)

3. Allure reports
   1. install allure
   2. run `allure generate`

4. Run via Selenoid
   1. `./cm selenoid start --vnc`
   2. `./cm selenoid-ui start` (optional)
   3. `pytest --executor={SELENOID_IP}` (or `pytest --executor=local` to run locally) 


## 2. Parser for `access.log` file. How-to:
Format must be the following:

`'91.113.11.120 - - [24/Sep/2019:21:16:13 +0200] "GET /apple-touch-icon-120x120-precomposed.png HTTP/1.1" 404 246 "-" "MobileSafari/604.1 CFNetwork/978.0.7 Darwin/18.7.0" 6203'`