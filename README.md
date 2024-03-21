# spiceai-fed-demo
A demo showcasing the federated SQL and acceleration capabilities of spiceai.

## Demo

0. Download and install the Spice.ai CLI

```bash
brew install spiceai/spiceai/spice
# or
curl https://install.spiceai.org | /bin/bash
```

1. Clone the repository

```bash
git clone https://github.com/phillipleblanc/spiceai-fed-demo.git
cd spiceai-fed-demo
```

2. Login to each data source

```bash
spice login # Logs into https://spice.ai
spice s3 login --access-key <access-key> --access-secret <secret-key>
spice postgres login --host <host> --port <port> --username <username> --password <password> --database <database>
```

3. Start the Spice.ai runtime

```bash
spice run
```

Now I have a running service that provides a unified SQL interface to my data sources. I also centralize storing the secrets needed to access my data sources, so my application becomes simpler. It also provides a natural connection pooler for backend DBs like Postgres.

Spice.ai natively uses Arrow for all operations - so it's fast, and applications can take advantage of a unified data model across all data sources. Query parquet files in S3, Postgres tables, and get all data in Arrow.

4. Show queries in `spice sql`

```bash
spice sql
sql> select table_name from information_schema.tables where table_schema = 'public'
sql> select * from s3_source
sql> select * from s3_source_accelerated
sql> select * from pg_source
sql> select * from spiceai_source
sql> select * from spiceai_source_accelerated
```

5. Walk through the yaml definition for each dataset and explain how it works