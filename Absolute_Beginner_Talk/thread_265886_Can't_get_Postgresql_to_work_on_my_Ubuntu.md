---
title: "Can't get Postgresql to work on my Ubuntu"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by itisgood on 2006-09-26
hi everyone,
im new to ubuntu, actually just finished dual boot installation last night.


i installed my postgresql trough <Add/Remove Applications>

the packages i have installed are 

< postgresql-8.1 >
< postgresql-client-8.1 >
< postgresql-client-common >
< postgresql-common >

but after it finished installation, i coulndn't log in to the database,

jyao@jyao-laptop:/$ psql
psql: FATAL:  database "jyao" does not exist
jyao@jyao-laptop:/$ psql postgres
psql: FATAL:  role "jyao" does not exist
jyao@jyao-laptop:/$ psql postgres -u
psql: Warning: The -u option is deprecated. Use -U.
User name: postgres
Password for user :
psql: FATAL:  Ident authentication failed for user "postgres"
jyao@jyao-laptop:/$ psql postgres -u
psql: Warning: The -u option is deprecated. Use -U.
User name: jyao
Password for user :<i typed pwd>
psql: FATAL:  role "jyao" does not exist
jyao@jyao-laptop:/$

is there any place that i should config?
and i also dont know how to start the actual server.

can anyone help me plz.....

thx a lot

---

### Post by hayalci on 2006-09-27
My /etc/postgresql/8.1/main/pg_hba.conf has this:```
local   all         all                                       password
host    all         all   127.0.0.1         255.255.255.255   password

```And you start the database by issuing ```
sudo /etc/init.d/postgresql-8.1 start
```

---

