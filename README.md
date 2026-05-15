# Local Microsoft SQL Server

Run SQL Server locally with Docker Compose.

```sh
docker compose up -d
```

On Windows, the same command works because the default password is already set in `docker-compose.yml`:

```cmd
docker compose up -d
```

Connection settings:

- Host: `localhost`
- Port: `1433`
- User: `sa`
- Password: `123456Qaz`

In SQL Server Management Studio, use SQL Server Authentication. If connection fails during the pre-login handshake, open **Options > Connection Properties** and enable **Trust server certificate**. Newer SSMS versions may also require setting **Encrypt** to **Optional** for a local Docker server.

On the first run, wait until the logs show `Recovery is complete` before connecting:

```sh
docker logs -f local-mssql
```

To use a custom password:

```sh
MSSQL_SA_PASSWORD='AnotherStrong!Passw0rd' docker compose up -d
```

Windows PowerShell:

```powershell
$env:MSSQL_SA_PASSWORD="AnotherStrong!Passw0rd"; docker compose up -d
```

Windows CMD:

```cmd
set MSSQL_SA_PASSWORD=AnotherStrong!Passw0rd && docker compose up -d
```

Check logs:

```sh
docker logs -f local-mssql
```

Stop the server:

```sh
docker compose down
```

Remove the database volume too:

```sh
docker compose down -v
```
