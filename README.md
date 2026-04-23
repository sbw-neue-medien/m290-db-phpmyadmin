# M290 Challenge – Probe

Docker-Compose-Setup für die M290-Prüfungsvorbereitung mit MariaDB und phpMyAdmin.

## Voraussetzungen

- [Docker](https://docs.docker.com/get-docker/) & Docker Compose

## Konfiguration

Umgebungsvariablen werden über die `.env`-Datei gesetzt:

| Variable              | Standardwert           | Beschreibung              |
|-----------------------|------------------------|---------------------------|
| `PROJECT_NAME`        | `m290_auftragsname`    | Projektname               |
| `MYSQL_ROOT_PASSWORD` | `rootpassword`         | Root-Passwort der DB      |
| `MYSQL_DATABASE`      | `${PROJECT_NAME}_db`   | Name der Datenbank        |
| `MYSQL_USER`          | `myuser`               | Datenbankbenutzer         |
| `MYSQL_PASSWORD`      | `mypassword`           | Passwort des Benutzers    |

> Vor dem ersten Start die `.env` an die eigenen Werte anpassen.

## Starten

```bash
docker compose up -d
```

## Dienste

| Dienst      | URL                      | Beschreibung               |
|-------------|--------------------------|----------------------------|
| phpMyAdmin  | http://localhost:8080    | Weboberfläche für MariaDB  |
| MariaDB     | localhost:3306           | Datenbankserver            |

## VS Code – Containers Extension

Mit der Extension [Containers](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-containers) können Docker-Container und -Images direkt aus VS Code verwaltet werden.

### Installation

1. VS Code öffnen
2. Erweiterungen (`Ctrl+Shift+X`) → nach **Containers** suchen → installieren  
   (Extension-ID: `ms-azuretools.vscode-containers`)

### Verwendung

Nach der Installation erscheint in der linken Seitenleiste das **Containers-Symbol** (Wal-Icon).

Dort sind folgende Bereiche verfügbar:

- **Containers** – zeigt alle laufenden und gestoppten Container; Rechtsklick ermöglicht Start, Stop, Logs anzeigen, Shell öffnen u. v. m.
- **Images** – lokale Docker-Images verwalten
- **Volumes** – persistente Volumes einsehen und löschen
- **Networks** – Docker-Netzwerke anzeigen

### Container-Shell öffnen

1. Docker Compose Stack starten (`docker compose up -d`)
2. In der Seitenleiste den gewünschten Container (z. B. `challange-mariadb-1`) rechtsklicken
3. **"Attach Shell"** wählen – ein integriertes Terminal öffnet sich direkt im Container

## Stoppen

```bash
# Container stoppen
docker compose down

# Container und Daten-Volume löschen
docker compose down -v
```
