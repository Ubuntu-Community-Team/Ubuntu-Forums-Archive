---
title: "Installing PostgreSQL 8.2 woes."
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by gezus on 2007-04-19
Dist,

 I now have PostgresSQL 8.1 and 8.2 fully uninstalled however when I re-install 8.2 only /usr/lib/postgresql /usr/share/postgresql are created, no /etc directories exist at all. 

But during the install no errors are produced at all.

If anyone has any insight it would be greatly appreciated.

Regards,
Sean.

---

### Post by saimonmoore on 2007-04-20
I've comes across the exact same problem. I initially installed postgresql-8.1 which  warned me that it was obsolete and that I should install 8.2. So I removed 8.1 with apt-get remove and then installed 8.2.

On first installation, I tried to connect to the server via:

sudo su postgres -c psql

but it kept trying to connect via a non existant unix socket based on port 5432 even though 5433 was set in postgresql.conf. After trying different things, I decided to remove the postgresql-8.2 package and reinstall.

Ever since that point, every time I try to reinstall 8.2 the etc files are not installed, only the /usr files.

---

### Post by saimonmoore on 2007-04-20
I should also mention that the same problem happens when trying to install postgresql-8.1.

example  output:

saimon@iris:~$ sudo apt-get install postgresql-8.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  postgresql-client-8.2 postgresql-client-common postgresql-common
Suggested packages:
  oidentd ident-server postgresql-doc-8.2
The following NEW packages will be installed:
  postgresql-8.2 postgresql-client-8.2 postgresql-client-common postgresql-common
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4535kB of archives.
After unpacking 22.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Selecting previously deselected package postgresql-client-common.
(Reading database ... 101279 files and directories currently installed.)
Unpacking postgresql-client-common (from .../postgresql-client-common_73_all.deb) ...
Selecting previously deselected package postgresql-client-8.2.
Unpacking postgresql-client-8.2 (from .../postgresql-client-8.2_8.2.3-3_i386.deb) ...
Selecting previously deselected package postgresql-common.
Unpacking postgresql-common (from .../postgresql-common_73_all.deb) ...
Selecting previously deselected package postgresql-8.2.
Unpacking postgresql-8.2 (from .../postgresql-8.2_8.2.3-3_i386.deb) ...
Setting up postgresql-client-common (73) ...
Setting up postgresql-client-8.2 (8.2.3-3) ...

Setting up postgresql-common (73) ...

Setting up postgresql-8.2 (8.2.3-3) ...



From dpkg.log:

2007-04-20 15:19:45 install postgresql-client-common 73 73
2007-04-20 15:19:45 status half-installed postgresql-client-common 73
2007-04-20 15:19:45 status unpacked postgresql-client-common 73
2007-04-20 15:19:45 status unpacked postgresql-client-common 73
2007-04-20 15:19:45 install postgresql-client-8.2 <none> 8.2.3-3
2007-04-20 15:19:45 status half-installed postgresql-client-8.2 8.2.3-3
2007-04-20 15:19:45 status unpacked postgresql-client-8.2 8.2.3-3
2007-04-20 15:19:45 status unpacked postgresql-client-8.2 8.2.3-3
2007-04-20 15:19:45 install postgresql-common 73 73
2007-04-20 15:19:45 status half-installed postgresql-common 73
2007-04-20 15:19:46 status unpacked postgresql-common 73
2007-04-20 15:19:46 status unpacked postgresql-common 73
2007-04-20 15:19:46 install postgresql-8.2 8.2.3-3 8.2.3-3
2007-04-20 15:19:46 status half-installed postgresql-8.2 8.2.3-3
2007-04-20 15:19:47 status unpacked postgresql-8.2 8.2.3-3
2007-04-20 15:19:47 status unpacked postgresql-8.2 8.2.3-3
2007-04-20 15:19:47 status unpacked postgresql-client-common 73
2007-04-20 15:19:47 status unpacked postgresql-client-common 73
2007-04-20 15:19:47 status half-configured postgresql-client-common 73
2007-04-20 15:19:47 status installed postgresql-client-common 73
2007-04-20 15:19:47 status unpacked postgresql-client-8.2 8.2.3-3
2007-04-20 15:19:47 status half-configured postgresql-client-8.2 8.2.3-3
2007-04-20 15:19:48 status installed postgresql-client-8.2 8.2.3-3
2007-04-20 15:19:48 status unpacked postgresql-common 73
2007-04-20 15:19:48 status unpacked postgresql-common 73
2007-04-20 15:19:48 status unpacked postgresql-common 73
2007-04-20 15:19:48 status unpacked postgresql-common 73
2007-04-20 15:19:48 status half-configured postgresql-common 73
2007-04-20 15:19:49 status installed postgresql-common 73
2007-04-20 15:19:49 status unpacked postgresql-8.2 8.2.3-3
2007-04-20 15:19:49 status unpacked postgresql-8.2 8.2.3-3
2007-04-20 15:19:49 status half-configured postgresql-8.2 8.2.3-3
2007-04-20 15:19:49 status installed postgresql-8.2 8.2.3-3

Notice: half-configured postgresql-8.2 8.2.3-3

---

### Post by saimonmoore on 2007-04-20
Hi,

I managed to solve this problem by:

* reinstalling postgresql-8.2 with:

```
sudo apt-get install postgresql-8.2 libpgsql-ruby1.8 postgresql-client-8.2 postgresql-client-common postgresql-common libpq4
```

* Removing using purge (to remove config files)

```
sudo apt-get --purge remove postgresql-8.2 libpgsql-ruby1.8 postgresql-client-8.2 postgresql-client-common postgresql-common libpq4
```

* reinstalling with:

```
sudo apt-get install postgresql-8.2 libpgsql-ruby1.8 postgresql-client-8.2 postgresql-client-common postgresql-common libpq4
```

---

### Post by Lars&#1758; on 2007-12-13
Hello Friends,

I am having experiencing extreme difficulty re-installing Postgresql 8.2.5 on my Xubuntu 7.10 distro. My eventual goal is to have Postgresql, PostGIS, and pgAdminIII working on my old box to be a GIS Server (Geographic Information Systems) ... but I'll get to the point.

At one point in time - when I first installed Postgresql 8.2.5 + PostGIS + pgAdminIII with Synaptic - I was able to connect to my PostgreSQL server through pgAdmin, create db's and everything.

Well, I re-installed Postgresql because I thought I needed to change some settings...yadda,yadda. And then the trouble hit!

What I'm experiencing is :

> LOG:  could not bind IPv4 socket: Address already in use
HINT:  Is another postmaster already running on port 5432? If not, wait a few seconds and retry.
WARNING:  could not create listen socket for "localhost"
FATAL:  could not create any TCP/IP sockets

...after trying to execute /usr/local/pgsql/bin/postgres -D /usr/local/pgsql/data

From what I understand, this is the step after ***initializing the database*** via [[COLOR="Blue"]http://www.postgresql.org/docs/8.2/interactive/install-short.html[/COLOR]]("http://www.postgresql.org/docs/8.2/interactive/install-short.html")> /usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data 

I have tried the advice given in the post above mine, here - but no worky either. I'm lost:confused:

A couple of other weird issues:
[LIST]
[*]I cannot find postmaster.pid to delete which was suggested at one point
[*]My /usr/local/pgsql/data seems to be missing some commands like ALTERUSER
[/LIST]

[SIZE="2"][COLOR="YellowGreen"]Please, please - I have no where else to go...I have scoured every Google search, every piece of PostgreSQL documentation, and more.[/COLOR][/SIZE][-o<[-o<

---

