# Système de Gestion de Bibliothèque

Application Spring Boot pour la gestion des livres et des auteurs d'une bibliothèque.

## Technologies Utilisées

- Java 17
- Spring Boot 3.2.0
- Spring Data JPA
- Base de données H2 (en mémoire)
- Swagger/OpenAPI pour la documentation
- Maven
- Lombok

## Fonctionnalités

1. **Gestion des Auteurs**
   - Créer un nouvel auteur
   - Lister tous les auteurs
   - Obtenir un auteur spécifique
   - Modifier les informations d'un auteur
   - Supprimer un auteur

2. **Gestion des Livres**
   - Créer un nouveau livre lié à un auteur
   - Lister tous les livres
   - Obtenir un livre spécifique
   - Afficher les livres d'un auteur spécifique
   - Modifier les informations d'un livre
   - Supprimer un livre
   - Rechercher des livres par titre
   - Pagination des résultats

## Installation et Exécution

1. Cloner le dépôt
2. Se placer dans le répertoire du projet
3. Lancer l'application avec Maven :
   ```bash
   mvn spring-boot:run
   ```

L'application sera accessible à : http://localhost:8080

## Documentation API

La documentation Swagger est disponible à : http://localhost:8080/swagger-ui.html

## Console H2

La console H2 est accessible à : http://localhost:8080/h2-console
- JDBC URL : jdbc:h2:mem:librarydb
- Utilisateur : sa
- Mot de passe : password

## Exemples d'Appels API

### Créer un Auteur

```bash
curl -X POST http://localhost:8080/api/authors \
  -H "Content-Type: application/json" \
  -d '{
    "firstName": "Jules",
    "lastName": "Verne",
    "biography": "Écrivain français"
  }'
```

### Créer un Livre

```bash
curl -X POST http://localhost:8080/api/books \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Vingt mille lieues sous les mers",
    "description": "Roman d''aventures",
    "isbn": "9781234567890",
    "publicationDate": "1870-01-01",
    "author": {
      "id": 1
    }
  }'
```

### Rechercher des Livres avec Pagination

```bash
curl "http://localhost:8080/api/books/search?title=les&page=0&size=10"
```

## Structure du Projet

```
src/
└─ main/
   ├─ java/com/library/
   │  ├─ controller/     # Contrôleurs REST
   │  ├─ model/         # Entités JPA
   │  ├─ repository/    # Repositories Spring Data
   │  ├─ service/       # Services métier
   │  └─ exception/     # Gestion des exceptions
   └─ resources/
      ├─ application.properties  # Configuration
      └─ data.sql               # Données initiales
```

## Fonctionnalités Bonus Implémentées

- ✅ Validation des champs
- ✅ Documentation Swagger en français
- ✅ Pagination
- ✅ Tests unitaires
- ✅ Recherche de livres
- ✅ Gestion des exceptions personnalisée
- ✅ Données de démonstration
