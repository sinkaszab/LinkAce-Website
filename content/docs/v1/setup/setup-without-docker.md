---
title: Setup without Docker
weight: 20
---

The application was developed with being used with Docker in mind. All following steps will try to work around this but cannot be guaranteed to work in every environment. Please remember that you need shell access to work with LinkAce.

### Requirements

* A Linux-based server with shell access
* **PHP 7.3, 7.4 or 8.0**, with the following extensions
    * BCMath
    * Ctype
    * Fileinfo
    * JSON
    * Mbstring
    * OpenSSL
    * PDO
    * Tokenizer
    * XML
* A database server with one of the following databases running:
    * MySQL 5.6+ (recommended)
    * PostgreSQL 9.4+
    * SQLite 3.8.8+ (not tested, may work)
    * SQL Server 2017+ (not tested, may work)
* Please consider using `utf8mb4_bin` as the database collation. Other collations like `utf8mb4_general_ci` may cause issues with different Unicode characters.

Older PHP versions will **not** be supported in any way. Please do yourself a favor and do not expose yourself, or your users to any risks by using an outdated PHP version.

### 1. Get the .zip file

Download the LinkAce .zip package from the [release page](https://github.com/Kovah/LinkAce/releases/latest).

Extract all files and place them wherever you need them. This obviously depends on how and where you want to run the
app.

### 2. Edit the .env file

Make a copy of the `.env.example` file and name it `.env`. Please do not change any values in it now!

### 3. Generate a secret key

Run the following command to generate a secret key for your application and prepare LinkAce for the setup:

```
php artisan key:generate
```

### 4. Point your web server to /public

For security reasons the application won't run from the base folder where you extracted the files to. Instead, point your web server to the `/public` directory in your LinkAce folder.

If you are using Apache, LinkAce already ships with a proper .htaccess file.

If you are using nginx, see the docker nginx configuration for guidance.

### 5. Run the built-in setup

Now open the URL pointing to LinkAce in your browser. The built-in setup should start. Follow the instructions to configure a database and register your user account.

{{< alert type="warning" >}}
Please make sure to follow the [post-installation steps]({{< relref path="docs/v1/setup/post-setup.md" >}}) to fully enable all features, including automated backups and link checks.
{{</ alert >}}

---

Next Step: [Post-Setup Steps]({{< relref path="docs/v1/setup/post-setup.md" >}})
