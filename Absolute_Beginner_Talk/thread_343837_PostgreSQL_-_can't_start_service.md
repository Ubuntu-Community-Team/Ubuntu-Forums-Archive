---
title: "PostgreSQL - can't start service"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by borland-c on 2007-01-22
yesterday I sets up PostgreSQL 7.4.13
It's work excellent for me yesterday
today I put on my conputer with Ubuntu Edgy
and while connection recieved error **Unable to connect to PostgreSQL server**```
$ sudo /etc/init.d/postgresql-7.4 start
 * Starting PostgreSQL 7.4 database server
```ever after this command I can't connect to postgresql```
psql: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/tmp/.s.PGSQL.5432"?
```any help will be good for me

---

### Post by jordanmthomas on 2007-01-22
does this open a postgres command prompt?
```
sudo postgres
```
If not, you may need to edit the postgresql configuration file (in /etc/postresql or something similar) and make sure it is listening on 127.0.0.1

If sudo postgres does do something, postgres is in fact running and you will need to create a user
```
createuser -P *yourname*
exit
```
then, you should be able to create databases as you need
```
createdb -O *yourname* database_name
```

Then, maybe try connecting to your postresql server from whatever program and give it your new database's name.
Is this at all helpful?

---

### Post by borland-c on 2007-01-22
```
$ sudo postgres
sudo: postgres: command not found
```what about listen - as far as I understand defaults - allow to anyone
but I add to */etc/postgresql/postgresql.conf* line **listen_addresses = 'localhost'**
and recieved new error _FATAL:  unrecognized configuration parameter "listen_addresses"_
I can't create new user```
createuser: could not connect to database postgres: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/tmp/.s.PGSQL.5432"?
```by the way - look PostgreSQL don't listen any port```
$ netstat -tl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp6       0      0 *:www                   *:*                     LISTEN     
tcp6       0      0 *:ftp                   *:*                     LISTEN
```

---

### Post by jordanmthomas on 2007-01-22
Well, I am not sure what the problem is.  Someone else may need to help.  Is there any reason you are using 7.4 instead of the latest?   Sorry man, but I'm not sure what else to try.

---

### Post by borland-c on 2007-01-22
[q]Is there any reason you are using 7.4 instead of the latest?[/q]
nope - I just start using PostgreSQL, hope it will be better than MySQL
by the way good idea - may be it is reason to get older fixed version
in any way thanks for attention

---

