# 🚂 TchouTchou

> Tableau de bord live pour les **ferroviphiles** — vitesse, GPS, itinéraire, qualité WiFi et plus encore, directement depuis le réseau bord SNCF.

![Standalone HTML](https://img.shields.io/badge/format-HTML%20standalone-blue) ![No server required](https://img.shields.io/badge/serveur-non%20requis-green)

---

## ✨ Fonctionnalités

- **Vitesse en temps réel** (km/h)
- **Temps restant** avant l'arrivée à destination
- **Destination & itinéraire** avec statut de chaque arrêt (à l'heure / retard / en cours)
- **Qualité du signal WiFi** (5 barres) et nombre d'appareils connectés
- **Boussole** avec cap en degrés
- **Carte interactive** (Leaflet) avec tracé du trajet et localisation du train
- **Fréquentation du bar** à bord
- **Mode démo** quand tu n'es pas dans le train
- Compatible **mobile** 📱
- Rafraîchissement automatique toutes les **10 secondes**

---

## 🚀 Utilisation

> ⚠️ Les APIs SNCF ne sont accessibles **que depuis le réseau WiFi du train**. Le dashboard n'affichera pas de données réelles hors connexion (un mode démo est disponible).

### 1. Télécharger le fichier

Clique sur **[index.html](./index.html)** puis **"Download raw file"** (ou clône le repo).

### 2. Ouvrir dans le navigateur

Connecte-toi au **WiFi SNCF** à bord du train, puis ouvre simplement le fichier :

```
Double-clic sur index.html  →  s'ouvre dans ton navigateur
```

Aucun serveur, aucune installation, aucune dépendance. Ça marche direct. ✅

### 3. Mode démo (hors train)

Si tu n'es pas connecté au WiFi SNCF, un écran s'affiche avec un bouton **▶ MODE DÉMO** pour visualiser le dashboard avec des données simulées (TGV Paris → Lyon).

---

## 📡 Sources & APIs utilisées

Toutes les données viennent des APIs du portail WiFi bord SNCF, accessibles uniquement sur le réseau local du train :

| Endpoint | Données |
|---|---|
| `https://wifi.sncf/router/api/train/gps` | Position GPS, vitesse, altitude, cap |
| `https://wifi.sncf/router/api/train/details` | Numéro de train, arrêts, horaires, retards |
| `https://wifi.sncf/router/api/connection/status` | Statut WiFi, débit, data restante |
| `https://wifi.sncf/router/api/connection/statistics` | Qualité signal, nb d'appareils |
| `https://wifi.sncf/router/api/bar/attendance` | Fréquentation du bar |

Ces endpoints ont été documentés et explorés grâce au projet open source **[sncf-wifi-portal-client](https://github.com/derhuerst/sncf-wifi-portal-client)** par [@derhuerst](https://github.com/derhuerst).

### Librairies front-end

| Librairie | Usage |
|---|---|
| [Leaflet.js](https://leafletjs.com/) | Carte interactive |
| [CartoDB Voyager tiles](https://carto.com/basemaps/) | Fond de carte |
| [Google Fonts – Inter & Orbitron](https://fonts.google.com/) | Typographie |

---

## 🛠 Pourquoi ouvrir en local ?

Le fetch des données se fait depuis **le navigateur** (pas un serveur). Les APIs SNCF acceptent les requêtes depuis `file://` (origin `null`) car c'est le même mécanisme que la page captive du portail à bord. Si tu héberges le fichier sur un serveur distant, le navigateur envoie un en-tête `Origin` que wifi.sncf rejette (CORS).

**→ Solution : télécharge `index.html`, ouvre-le directement dans ton navigateur sur le réseau WiFi SNCF.**

---

## 📄 Licence

MIT — fais-en ce que tu veux, partage-le dans ton wagon 🚃
