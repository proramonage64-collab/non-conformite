# Diagnostic Fumisterie — ProRamonage 64

Application web de visite ramonage / fumisterie : on photographie l'installation, l'appli sort les non-conformités et un rapport client.

## Deux modes

- **Express** (5 à 10 min) : photos seulement. L'analyse IA trie les photos par zone, déduit le type d'appareil, de conduit et de toiture, et liste les non-conformités.
- **Complet** (20 à 30 min) : zone par zone (appareil, raccordement, té & plaque, hotte, conduit, amenée d'air, sortie de toit) avec photos guidées, mesures et constats facultatifs. Les règles chiffrées tournent en direct.

Quand une info manque, l'appli fait sans : la règle ne se déclenche pas, ou elle prend le cas le plus courant et le précise dans le constat.

## Références intégrées

NF DTU 24.1 (éd. 2020), NF DTU 24.2, arrêté du 22/10/1969 (art. 18 débouchés), arrêté du 23/02/2009 (amenée et sortie d'air, CO), RSDT art. 31, CPT 3615 (VMC hygro), décret 2023-641 (ramonage), avis techniques fabricants (lecture de la désignation : G50 = 50 mm).

## Mise en ligne sur GitHub Pages

1. Créer un dépôt (ex. `diagnostic-fumisterie`) et y déposer `index.html` et ce `README.md`.
2. Settings → Pages → Source : « Deploy from a branch », branche `main`, dossier `/ (root)` → Save.
3. L'appli est en ligne après une minute à l'adresse `https://<compte>.github.io/diagnostic-fumisterie/`.
4. Sur le téléphone : ouvrir l'adresse puis « Ajouter à l'écran d'accueil ».

## Analyse IA des photos

Hors de Claude, l'analyse appelle directement l'API Anthropic :

1. Créer une clé sur https://console.anthropic.com (API Keys) et ajouter un peu de crédit.
2. Dans l'appli : **Accueil → Analyse IA des photos**, coller la clé, Enregistrer.

La clé est stockée uniquement dans le navigateur du téléphone. **Ne jamais écrire la clé dans le code publié sur GitHub** (le dépôt public serait lisible par tous). Modèle utilisé : `claude-sonnet-5-5` (constante `MODEL` dans `index.html`). Chaque analyse est facturée sur le compte API (quelques centimes par lot de photos).

Sans clé, tout le reste fonctionne : règles chiffrées, rapport, export.

## Données

- Les réponses et mesures sont gardées dans le navigateur (localStorage).
- Les photos restent en mémoire le temps de la visite : **télécharger le rapport avant de fermer la page** (fichier HTML avec photos, imprimable en PDF).
