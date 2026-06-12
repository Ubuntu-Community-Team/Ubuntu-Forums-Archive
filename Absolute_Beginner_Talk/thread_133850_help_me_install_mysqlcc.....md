---
title: "help me install mysqlcc...."
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by bbqbaker on 2006-02-20
It seems like the package i downloaded from mysql, somehow, i am missing some files. here are my output when running the ./configure...thanks for the help!:

checking build system type... i686-pc-linux-g++
checking host system type... i686-pc-linux-g++
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for compress in -lz... no
checking for libmysqlclient...
checking for "/usr/lib/libmysqlclient.a"... no
checking for "/usr/lib/mysql/libmysqlclient.a"... no
checking for "/usr/local/lib/libmysqlclient.a"... no
checking for "/usr/local/lib/mysql/libmysqlclient.a"... no
checking for "/usr/local/mysql/lib/libmysqlclient.a"... no
configure: error: Could not find libmysqlclient in ' /usr/lib /usr/lib/mysql                 /usr/local/lib /usr/local/lib/mysql                    /usr/local/mysql/lib'

---

### Post by gord on 2006-02-20
id suggest downloading mysql from synaptic as that will resolve your dependancys for you (which is the problem you are having, mysql relays on other software which you don't have)

---

### Post by bbqbaker on 2006-02-21
hi, i took your suggestion and just did a couple uninstall and reinstall/update on the mysql packages. now everything is working fine thanks to synaptic

[QUOTE=gord]id suggest downloading mysql from synaptic as that will resolve your dependancys for you (which is the problem you are having, mysql relays on other software which you don't have)[/QUOTE]

---

### Post by chantra on 2006-02-22
if you like, i made a mysqlcc package you can get this link: [mysql cc .deb package]("http://debuntu.org/2006/02/12/3-mysqlcc-094")

---

### Post by be4truth on 2008-04-03
> **chantra said:**
> if you like, i made a mysqlcc package you can get this link: [mysql cc .deb package]("http://debuntu.org/2006/02/12/3-mysqlcc-094")

This package need gcc 4.0 which I can't install on Gutsy. Any idea how to get a mysqlcc version on gutsy 32 bit?

Thx for help

Found it myself

[http://wiki.bluelightav.org/display/BLUE/MySQL+database]("http://wiki.bluelightav.org/display/BLUE/MySQL+database")

---

