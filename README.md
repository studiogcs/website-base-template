# Website base template
This is a skeleton project for a dockerized Django web app. It mostly draws from Michael Herman's [Dockerizing Django with Postgres, Gunicorn and Nginx](https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/), with minor structure changes and additions. The final setup includes a generic website ("blog") with separate "homepage" app. The purpose is to accelerate website development using Django, Postgres, Docker, Gunicorn, Nginx. 

Individual portions can be viewed on the following separate branches. 

## 0. Local development environment setup
This branch contains the setup for basic Docker containers serving Postgres and the Django web app. The user needs to create a local .env.dev file with the following environment variables:

```
SECRET_KEY = <custom key for development>
DEBUG=1
DJANGO_ALLOWED_HOSTS=localhost 127.0.0.1 [::1]
SQL_ENGINE=django.db.backends.postgresql
SQL_DATABASE=<custom name>
SQL_USER=<custom user name>
SQL_PASSWORD=<custom database password>
SQL_HOST=db
SQL_PORT=<database port>
DATABASE=postgres
```

To run and quit the container:
```
$ docker-compose up -d --build
$ docker-compose -f docker-compose.yml down -v
```

## 1. Remote production environment setup
This branch contains the setup for both the development and production Docker containers. As before, the user needs to create .env.dev, .env.prod and .env.prod.db files. See [Dockerizing Django with Postgres, Gunicorn and Nginx](https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/) for more info.

To run and quit the container:
```
$ docker-compose -f docker-compose.prod.yml up -d --build
$ docker-compose -f docker-compose.prod.yml down -v
```

## 2. Website development
This branch provides the very first steps in creating a homepage, with a single index.html file. Containers can be run using the same commands as in the remote production environment setup. 

# What's not provided
- Let's Encrypt and other security measures

# Requirements
- git
- Docker

# Resources

- [Using mkvirtualenv to create new Virtual Environment – Python](https://www.geeksforgeeks.org/using-mkvirtualenv-to-create-new-virtual-environment-python/) (2020)
- [Using Python environments in VS Code](https://code.visualstudio.com/docs/python/environments#_create-a-virtual-environment) (2021)
- [Dockerizing Django with Postgres, Gunicorn and Nginx](https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/) (2021)
- [Github Documentation](https://docs.github.com/en)
- [Create a homepage in Django](https://medium.com/@9cv9official/how-to-set-up-your-homepage-with-django-ae21f439c8a3)
