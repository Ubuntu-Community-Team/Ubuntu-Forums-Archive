---
title: "Oracle 10g xe sqlplus settings?"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by dross on 2006-12-17
Hi,
Does anyone know if there is a way to change the default settings for oracle 10g xe sqlplus?    For some reason, when I hit the up key, I'm not getting old commands that I've entered  (as I get in the shell).  Also, all columns are defaulting to the maximum character length, which makes most tables impossible to read without formatting columns..I seem to remember sqlplus shortening columns by default when I used it in windows...Any one have similar problems? or know how to fix these?

---

### Post by dross on 2006-12-19
After some searching, I found that sqlplus for linux doesn't have command history buffer...too bad.  But I also found a tool that seems to deal with it (haven;t used it yet, so can;t vouch for the performance, but it definitely has command history):  [gqlplus]("http://gqlplus.sourceforge.net/").  As the directions state, setup is pretty easy (I'm going to spell out what I did because it took me a few tries to get it to work):  

after you download gqlplus,

1. find your path variable:

```
echo $PATH
```

you should see this path in there:

```
/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin
```

if you don't, you should follow[this tutorial]("https://help.ubuntu.com/community/Oracle10g#head-35cee01075d83fad1bb353beac13b27bda3fee32") to edit .bashrc to put sqlplus in path (unless you have a custom configuration...in which case you probably wouldn't be looking here for direction) 

2.  take out the gqlplus executable from the download:  gqlplus-1.12/Linux/gqlplus

3.  place the executable in any of the path directories (probably makes sense to put it in the oracle xe path...or at least that;s what I did) and you should be able to access gqlplus with gqlplus command:

```
gqlplus
```

---

### Post by troach on 2006-12-21
To change the default behavior of your columns, issue this command in sqlplus

COLUMN column_name FORMAT A20

Where 20 is the width of column column_name. You could make it anything you'd like.

Also, download and use SQL DEVELOPER 1.1 from Oracle. I got it to install on Ubuntu, and it connected to my XE database for a smoother development IDE. Even includes debugging and best of all it's free!

Make sure after installing it somewhere you issue a chmod +x on the sqldeveloper executable which is buried deeper in the program. They have a shell script higher up that calls it. The ecxecutable is in a bin folder. I had it installed in about 10 minutes and it is sweet! Go to otn.oracle.com to download it.

---

### Post by dross on 2006-12-21
Cool, so its like Eclipse, but with built-in xe connectivity?

---

### Post by lamego on 2006-12-21
dross,
SQL Develoepr is for database development it has nothing to do with Eclipe which is generic IDE, more used for Java.

---

### Post by fergs on 2007-05-16
looking at installing sqldeveloper but cannot find for ubuntu. 
oracle website have an rpm - am i meant to extract files from this!!

can not find zip file which i've seen discussed elsewhere.

I'm running Ubuntu Studio with Oracle XE - all running sweet

any help would be appreciated.

---

### Post by MatthewAPeters on 2007-09-14
Go to:

[http://www.oracle.com/technology/software/products/sql/index.html](http://www.oracle.com/technology/software/products/sql/index.html)

Choose:

Oracle SQL Developer for Multiple Platforms (you must create account/agree to terms/other non-linuxy stuff before downloading)

Its java-based, so you don't need to do anything special other than untar it (unless you are using Compiz or Beryl desktops, which don't get along with Swing - but that is another thread).  As I pointed out to a co-worker, you need to execute the sqldeveloper.sh, not the sqldeveloper.exe if you want it to work in Ubuntu.....

Have fun!

Matt


> **fergs said:**
> looking at installing sqldeveloper but cannot find for ubuntu. 
oracle website have an rpm - am i meant to extract files from this!!

can not find zip file which i've seen discussed elsewhere.

I'm running Ubuntu Studio with Oracle XE - all running sweet

any help would be appreciated.

---

### Post by MatthewAPeters on 2007-09-14
Hope this isn't seen as too out-of date, but there is an alternative to gqlplus:  install rlwrap (sudo apt-get install rlwrap)  and invoke it before sqlplus like so:

rlwrap sqlplus user/pwd

you will get history with up and down arrow keys, home and end with their respective keys, and delete will actually delete.  No tab completion, but then, I haven't found gqlplus' tab completion truly context-sensitive.

Matt

> **dross said:**
> After some searching, I found that sqlplus for linux doesn't have command history buffer...too bad.  But I also found a tool that seems to deal with it (haven;t used it yet, so can;t vouch for the performance, but it definitely has command history):  [gqlplus]("http://gqlplus.sourceforge.net/").  As the directions state, setup is pretty easy (I'm going to spell out what I did because it took me a few tries to get it to work):  

after you download gqlplus,

1. find your path variable:

```
echo $PATH
```

you should see this path in there:

```
/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin
```

if you don't, you should follow[this tutorial]("https://help.ubuntu.com/community/Oracle10g#head-35cee01075d83fad1bb353beac13b27bda3fee32") to edit .bashrc to put sqlplus in path (unless you have a custom configuration...in which case you probably wouldn't be looking here for direction) 

2.  take out the gqlplus executable from the download:  gqlplus-1.12/Linux/gqlplus

3.  place the executable in any of the path directories (probably makes sense to put it in the oracle xe path...or at least that;s what I did) and you should be able to access gqlplus with gqlplus command:

```
gqlplus
```

---

