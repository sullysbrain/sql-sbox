# Installation

Notations for SQL work, specifically with PostgreSQL on MacOS / terminal and a bit of linux (ubuntu).

```
brew install postgress@16
```

If you are upgrading, stop the old postgres service:
```
brew services stop postgresql@14
```

Export the path as mentioned in the output of the command above, in my case: 
```
echo 'export PATH="/opt/homebrew/opt/postgresql@16/bin:$PATH"' >> ~/.zshrc
```

The ressource .zshrc: 
```
source ~/.zshrc
```

Upgrade your PostgreSQL data directory, in my case:

    pg_upgrade \
    -d /opt/homebrew/var/postgresql@14 \
    -D /opt/homebrew/var/postgresql@16 \
    -b /opt/homebrew/opt/postgresql@14/bin/ \
    -B /opt/homebrew/opt/postgresql@16/bin/

Start the service for the new version, in my case: 
```
brew services start postgresql@16
```

Uninstall the old version (if you want), in my case: 
```
brew uninstall postgresql@14
```



## Start postgres
    brew services start postgresql@16
    brew services stop postgresql@16
    brew services restart postgresql@16


## Add user "postgres"
    createuser -s postgres



## List to see if postgres is running
    brew services list


## Start Postgress as 'postgres' user
    psql postgres

##
    CREATE ROLE pgUser WITH LOGIN PASSWORD 'password';
    ALTER ROLE pgUser CREATEDB;

    \q

    psql postgres -U pgUser

    \du



## CLI commands

Run SQL from the command line:
    psql -U postgres -d sqlda -c "SELECT first_name FROM customers WHERE state = 'AZ'";

Run SQL from a .sql file:
    psql -U postgres -d sqlda -a -f sqlda_test_main.sql



# TODO:
migrate to linux server

