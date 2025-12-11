# analyse_march-_immobilier
Bienvenue dans le projet **Locamoi Scraper** – un outil qu'on a développé pour explorer et comprendre le marché immobilier français de manière simple et interactive

L’idée est née d’un constat : les plateformes immobilières offrent une tonne de données, mais rarement de manière structurée et exploitable. Ce projet automatise la collecte de ces données, les nettoie et les rend **visuellement accessibles**

# Grâce à ce projet, il est possible de :
Visualiser les zones où les prix sont les plus élevés
Comparer la moyenne du prix au m² par ville ou région
Identifier rapidement les biens correspondant à un budget et à une surface donnée
Exporter les données vers Power BI ou Excel pour des dashboards personnalisés

## Les objectifs du projet
- Extraire **toutes les annonces de Locamoi.fr** pour un ensemble de villes préfectures
- Normaliser et **nettoyer les données** pour en faciliter l’analyse
- Fournir des visualisations **interactives**, notamment une carte Folium pour situer chaque bien

## 🧩 Pourquoi ce projet est intéressant
- Il combine **scraping, data cleaning et visualisation** dans un workflow complet.
- Il montre comment **transformer des données brutes d’un site web en insights exploitables**.
- Il permet de répondre à des questions concrètes comme :
  - la moyenne du prix au m² dans ma ville 
  - Quelle surface puis-je obtenir pour mon budget dans différentes régions ?
  - Où se concentrent les biens les plus chers ?
 
## 🧠 Architecture et workflow
1️⃣ constants.py
Contient la liste des villes et régions, les types de biens, et les URLs
Fournit la fonction slugify_city pour transformer un nom de ville en URL compatible

2️⃣ scraper.py
Parcourt toutes les villes et tous les types de biens
Récupère le titre, prix, surface, localisation et type de chaque annonce
Stocke le tout dans un CSV brut

3️⃣ clean_data.py
Supprime les doublons et valeurs aberrantes
Convertit les données en formats exploitables (prix en int, surfaces en m², types normalisés)
Produit un CSV propre prêt pour analyse et visualisation

4️⃣ map.py
Charge les données nettoyées.
Crée une carte interactive Folium, centrée sur la moyenne des coordonnées.
Chaque bien est représenté par un point cliquable, avec tooltip et popup pour les infos détaillées.
Sortie : carte_biens_locamoi.html

5️⃣ Dashboard interactif 
- Permet à l’utilisateur de filtrer les biens selon : ville ou région, type de bien, surface, prix, nombre de pièces
- Affiche des **graphiques dynamiques** (distribution du prix au m², corrélation surface/prix)
- Carte interactive mise à jour selon les filtres
- Sortie : exploration facile des données

🧪 Tests & qualité
Logs intégrés
Gestion des erreurs réseau
Vérification des champs essentiels (prix, type, surface)
Slugs contrôlés via constants.py
