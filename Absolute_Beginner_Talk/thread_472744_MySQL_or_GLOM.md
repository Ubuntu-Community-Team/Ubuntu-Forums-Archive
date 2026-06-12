---
title: "MySQL or GLOM"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by linuxforrealpeople on 2007-06-13
I have a relatively straightforward database application to create, something that I would have created using MS Access. It does require some programming to calculate values and import csv files.

Having done some research it seems like two of the strongest contenders are MySQL and Glom. Tough question but would anyone like to expresss a preference.

Thanks.

---

### Post by ccfjeff on 2007-06-13
> **linuxforrealpeople said:**
> Having done some research it seems like two of the strongest contenders are MySQL and Glom. Tough question but would anyone like to expresss a preference.

Thanks.

I would be interested in this as well as I would like to continue to work on a database for my small business.  I started designing it in Access, but would like to import it to a Linux application.

Is there a reason you don't include OO's Base database application among your "strongest contenders" list?  What are it's drawbacks as you see them vis a vis MySQL or Glom?

---

### Post by gezus on 2007-06-13
I would say Postgre is the way to go.
For no reason other than it's my fav.

---

### Post by linuxforrealpeople on 2007-06-13
I had a look at Base and it looks weak to me. I managed to break it without even trying.

---

### Post by mlentink on 2007-06-13
Quite frankly your choice of the final two puzzles me a bit. 
I don;t know GLOM, but reading about it it seems like it's a database frontend. A tool to develop database in ProgresSQL in. 
MySQL is a complete database system, just like Postgres is. So to be fair, you have to look at a MySQL frontend as well.

Am I mistaken?

---

### Post by EndPerform on 2007-06-13
I guess it depends on what you want it to do, exactly.  OOBase may work, but if you want to be more flexible, certainly look into mySQL or Postgres.  If you're going to code anyway, you could toss a web frontend on your app and centralize it as well, but again, I don't know what the app is doing, and this might be overkill for you.  OOBase is the closest you're going to get to Access, however.

---

### Post by linuxforrealpeople on 2007-06-13
Thank-you all for your thoughts.

I have installed MySLQ usng apt get apparently successfully but it has not attached itself to a menu. Can anyone please tell me how I start it up?

---

### Post by EndPerform on 2007-06-20
> **linuxforrealpeople said:**
> Thank-you all for your thoughts.

I have installed MySLQ usng apt get apparently successfully but it has not attached itself to a menu. Can anyone please tell me how I start it up?

MySQL starts when you boot the machine, using an init script.  There's no pretty front-end for it by default.

---

### Post by kevdog on 2007-06-20
Use synaptic or aptitude and grab phpmyadmin.  It gives you a reasonable good GUI frontend for mySQL.  To my knowledge however its not a lot like Access.

---

### Post by st0nes on 2007-06-20
While we're talking about databases, has anyone tried Aubit?  I am an Informix developer (4gl) and would like to write 4gl apps for Postgres.  I'm having some difficulty getting Aubit working, though.

---

### Post by hyper_ch on 2007-06-20
Well, depending on your needs you also may want to consider SQLite...

---

### Post by niteshifter on 2007-06-20
Hi, 

> I have installed MySLQ usng apt get apparently successfully but it has not attached itself to a menu. Can anyone please tell me how I start it up?

As EndPerform said, it starts when your system starts. It's a service - it's waiting for a process to connect to it. If you're serious about MySQL goto to their website ([http://www.mysql.com](http://www.mysql.com)) and and view the manual online or download the pdf - MySQL is a quite a capable database suite, with many, many features. You'll really want that info close to hand:p

You need to download (at least with Edgy I did) from the repositories two additional packages for GUI access:

mysql-admin
mysql-query-browser

otherwise you have just the CLI client "mysql", which talks to the server app "mysqld". After installing the GUI tools you should see in your Applications menu under System Tools "MySQL Administrator", under Programming "MySQL Query Browser".

You can use the CLI client to do anything that the GUI admin tool will do, but it is tedious. There's a man page for it:

```
who@where:~$ man mysql
```

but I urge you to get the manual from mysql.com, it has a nice getting started section.

Also: this may be fixed in Fiesty but with the version available to Edgy there's a problem in MySQL Administrator. User Adminstration will appear not to work. It's fixable by a simple script, start gedit and copy the text below into it:

```
#!/bin/bash
export DEBUG_DONT_SPAWN_FETCHES=1
mysql-admin

```

Save it with the name mysql-admin-fixed.sh in your home directory. Change the permissions to execute. Then change the properities of the Applications/Programming menu item by going to System, Preferences, Menu Layout and click on System Tools to bring up that meun list. Right click on MySQL Administrator, click on Properties and change the Command box entry to wherever you saved mysql-admin-fixed.sh.

BTW, don't give up on OOBase just yet - it can connect to your MySQL database.

HTH

---

