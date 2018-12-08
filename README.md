# Générateur de site statique

Ceci est un projet proposé à des étudiants en Python.

## Qu'est-ce qu'un site statique

Un site internet statique est un site composé uniquement de fichiers présents dans un dossier :

* des fichiers HTML,
* des fichiers CSS,
* des fichiers JavaScript,
* des images,
* des vidéos,
* …

Cela s'oppose aux sites internet dynamique, où certains de ces fichiers sont générés à la volée par du logiciel, à partir par exemple de données dans une base de données.

## Héberger un site statique

Héberger un site dynamique est plus complexe que pour un site statique, il faut en effet installer le logiciel qui va générer les fichiers à la volée. Par contre, héberger un site statique est relativement simple, il suffit d'avoir un petit serveur web qui met à disposition le dossier contenant les fichiers statiques.

### Github

Github fournit un hébergement gratuit de site statique. Il suffit de créer un dépôt git avec Github, et de commiter dans une branche spécifique. Votre site est alors accessible à l'adresse suivante : https://votre_login.github.io/votre_nom_de_depot/

Plus de renseignement sur :

* https://pages.github.com/
* https://www.christopheducamp.com/2013/12/21/demarrer-avec-pages-github/
* https://developer.mozilla.org/fr/docs/Apprendre/Utiliser_les_pages_GitHub
  
### Utiliser un serveur web

Des outils commes Apache ou Nginx permettent de rendre accessible votre site par internet ou intranet :
* https://httpd.apache.org/docs/trunk/fr/getting-started.html
* http://sametmax.com/servir-des-fichiers-statiques-avec-nginx/
* https://doc.ubuntu-fr.org/nginx
* https://nginxconfig.io/

Python vous fournit un serveur web minimaliste, par exemple pour aller sur http://localhost:8080/ et y voir le site statique dont les fichiers sont dans `./dossier_de_mon_site/`.

```
python -m http.server 8080  --directory ./dossier_de_mon_site/
```

## Génerer un site statique

Les fichiers compris par un navigateur internet sont aux formats HTML/CSS/JavaScript. Vous n'avez peut-être pas envie de taper du HTML quand vous écrivez un blog. Il serait pratique de générer les pages web à partir d'un format textuel simple, comme le markdown (https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf), langage utilisé pour écrire le document que vous lisez actuellement (https://raw.githubusercontent.com/vpoulailleau/site_statique/master/README.md).

Certains outils open-source le font déjà, dont certains connus et en Python :

* https://blog.getpelican.com/
* https://www.getlektor.com/
* https://www.mkdocs.org/
* https://github.com/eudicots/Cactus
* http://www.sphinx-doc.org/en/master/
* https://www.getnikola.com/

## Projet

Vous allez réaliser un outil convertissant un dossier de fichiers markdown et d'images en un autre dossier contenant les fichiers d'un site statique. Du HTML sera généré à partir du markdown, et cet HTML sera mélangé avec des modèles de pages web pour générer des pages toutes conformes au même modèle (par exemple avec le même logo, le même sommaire de site internet, le même fichier CSS référencé…).

Les fichiers markdown peuvent être créés :

* avec Visual Studio Code
* avec https://github.com/ncornette/Python-Markdown-Editor
* avec https://pandao.github.io/editor.md/en.html
* avec https://dillinger.io/
* …

### Réalisation d'une interface en ligne de commande

Vous allez réaliser un outil en ligne de commande. Il prendra au moins comme paramètres :

* le chemin du dossier de fichiers
* le chemin du dossier où seront mis les fichiers générés
* éventuellement le dossier contenant des modèles de pages web à compléter
* de l'aide pour exliquer les paramètres de la commande

Vous pouvez utiliser :

* sys.argv (mais je ne vous le conseille pas)
* argparse (https://docs.python.org/fr/3/howto/argparse.html)
* click (https://click.palletsprojects.com/en/7.x/)

### Conversion de markdown vers HTML

Vous devez au moins convertir les syntaxes suivantes :
 
* `#`, un titre de niveau 1 en `<h1>`
* `##`, un titre de niveau 2 en `<h2>`
* `###`, un titre de niveau 3 en `<h3>`
* Convertir les listes non ordonées en `<ul>` et `<li>`
* Convertir les URL (http://quelquechose.com) en `<a href="http://quelquechose.com">http://quelquechose.com</a>`
* `*un texte*`, un texte important en `<em>un texte</em>`

Vous pouvez faire ces conversions en utilisant au choix :

* les fonctions de base de Python pour les chaînes de caractères
* les expressions régulières (https://docs.python.org/fr/3/library/re.html)
* un package de la communauté
  * https://github.com/Python-Markdown/markdown
  * https://github.com/trentm/python-markdown2

### Rendu sur Github

Votre projet Python sera posté sur Github et un lien sera fourni.

### Projet open-source

Vous pouvez faire un projet open-source. Beaucoup de projets Python utilisent la license MIT ou BSD 3 clauses, ces licences sont faciles à lire et très permissives. Vous pouvez aussi utiliser une licence plus stricte comme la GPL qui imposent que les versions modifiées de votre projet soient aussi open-source.

Vous pouvez faire en sorte que votre projet soit installable par la communauté Python en le diffusant sur le Python Package Index (https://pypi.org/).

Pour vous aidez dans cette aventure, vous pouvez utiliser https://github.com/audreyr/cookiecutter-pypackage.