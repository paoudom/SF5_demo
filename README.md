# Création rapide d'un projet Symfony 5

>Création d'un projet Symfony comprenant les bases pour commencer un nouveau projet :
>- La gestion des utilisateurs (module security)
>- Un template de base avec Bootstrap 5 (css uniquement)

`symfony new --full [nom_du_projet]`

Creer fichier .env.local et modifier la configuration de la base de données

`DATABASE_URL="mysql://root:@127.0.0.1:3306/sf_react?serverVersion=5.7"`

```yaml
doctrine:
    dbal:
        override_url: true
        url: '%env(resolve:DATABASE_URL)%'
        charset: utf8mb4
```

php bin/console doctrine:database:create


twig:
    default_path: '%kernel.project_dir%/templates'
    form_themes: ['bootstrap_5_layout.html.twig']


<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-eOJMYsd53ii+scO/bJGFsiCZc+5NDVN2yr8+0RDqr0Ql0h+rP48ckxlpbzKgwra6" crossorigin="anonymous">


<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container">
        <a class="navbar-brand" href="{{ path('home') }}">Symfony React</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
            <li class="nav-item">
            <a class="nav-link" href="">Un lien</ul>
        </div>
    </div>
</nav>


php bin/console make:controller HomeController

Modifier la route 'home' @Route("/", name="home")


symfony server:start


# config/packages/security.yaml
security:
    enable_authenticator_manager: true
    # ...

php bin/console make:user

retirer anonymous

composer require orm-fixtures --dev

php bin/console make:fixtures

modifier UserFixtures

php bin/console doctrine:fixtures:load

php bin/console make:auth


