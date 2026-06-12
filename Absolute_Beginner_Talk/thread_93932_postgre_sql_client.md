---
title: "postgre sql client"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by aran384 on 2005-11-23
ive installed the postgre sql client and i dont know what the command is to start it up...

it also hasnt seem to added to my applications menu or my debian menu where everything i install is ment to be in .,...


does any1 know the command to start it ,,,

thanks :)

---

### Post by matthewstory on 2005-11-23
It won't be in the menu because it is only has a CLI (command line interface).  To start up a postgresql db is a little more complicated.

If this is your first time using this instance of PostgreSQL then you'll need to initialize a database cluster using the initdb command.  To do this open a terminal window and type:

$ initdb -D /usr/local/pgsql/data

or whatever directory you want your database to be stored in.  

After you've done this you need to start up the postmaster to communicate with the postgresql database cluster that you've just created, to do this you'll need to type the following command into a terminal window:  

$ postmaster -D /usr/local/pgsql/data

This command will most likely turn the terminal window into a log, and you won't be able to use that instance of the window anymore, so open a new terminal window and you'll need to create a particular database within the cluster, this can be done with the following command:

$ createdb mydb

Once you've done this you can access your database through the psql program by typing:

$ psql mydb

You can also access this database through GUIs like PGAdmin III etc.  In general this question can be better answered in the future by looking at the very well constructed and documented website [www.postgresql.org](www.postgresql.org) .  Their documentation on the page is quite remarkable for an open source project.  You may also want to subscribe to the PostgreSQL listhosts particularly the general listhost, which you can also do through their website.  If these commands don't work it's most likely that the program wasn't installed correctly, but it could be a myriad of other things as well, so if you have problems post the error messages up here.

cheers,
matt

---

### Post by aran384 on 2005-11-23
think you got the wrong idea.... 

im after the postgre sql client program... its in the package manager, as a control center... 

i didnt install postgre sql ... i install the client but i dont know command to start it...

---

### Post by kont.raen on 2005-11-23
[QUOTE=aran384]think you got the wrong idea.... 

im after the postgre sql client program... its in the package manager, as a control center... 

i didnt install postgre sql ... i install the client but i dont know command to start it...[/QUOTE]

hmmm - the Client you need to connect to a database, running on a PostgreSQL database-server (postmaster is the server's process/daemon name) is named psql; and as [Matthewstory]("http://www.ubuntuforums.org/member.php?u=54585") already pointed out, it is a cli app - meaning that you need to open a terminal to start the app / get psql's connect options (man psql or psql --help).

---

### Post by abhaysahai on 2006-02-19
Use a easy to use client like "pgadmin3" it has a good GUI admin tool along with query editor. 
Indeed easy to use and very effective. 
It will not get added to Applications programming you need to expilicitly add the menu entry, but u can always run it from terminal 
pgadmin3

Hope this helps.
Abhay

---

### Post by jrevillini on 2006-03-13
thanks abhaysahai, that's exactly what i needed.

peace,
jim

---

### Post by murex on 2006-05-05
Can someone explain how can i log in my database with pgadmin3? I've created a database alreadey with createdb command. 
I give 
address: localhost (i've tried 127.0.0.1 and 192.168.0.2 too)
description: db
Service: I 'dont know what to put here
Port: 5432  SSL: nothing
initial DB: the database i've created
username: myusername
password: mypass

i get Error connecting to the server: FATAL:  password authentication failed for user "user"
Do i have to set another password and where?

Edit: Nevermind, found it.
I've changed in /etc/postgresql/8.1/main/
pg_hba.conf
#host    all         all         127.0.0.1/32          md5
[COLOR="Red"]host 	all	    all		127.0.0.1/32	      trust[/COLOR]

---

