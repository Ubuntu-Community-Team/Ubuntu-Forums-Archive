---
title: "Mysql &amp; Amarok"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by jrgibb on 2007-07-05
Ok, 

I've got Mysql 5.0 installed, I want to create a database for Amarok, to be honest not quite sure what to do next, I think there may be some permission issues as when I type mysql in the terminal I get the following error;

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Help :(

J

---

### Post by tartarian on 2007-07-05
Heya!
Have a look at the Amarok Wiki. There's a guide I think
[HERE]("http://amarok.kde.org/wiki/MySQL_HowTo")

---

### Post by moredhel on 2007-07-05
When I use that guide I make the database etc (this happens with postgresql as well btw), I can connect with mysql admin and mysql browser, but amarok says it can't connect, and this is with the exact same connection info.

Sorry, if i'm hiijacking this thread btw :(

But anyone know why this is happening?

---

### Post by jrgibb on 2007-07-05
Simply can't connect to the database, I've looked at and tried some of the early steps in the guide but am getting nowhere, I really need a step by step guide (real newbie).

J

---

### Post by tartarian on 2007-07-05
Which bit are you getting stuck at?
Can't say I'm a total expert at this either 
But I'll try and give you a hand

---

### Post by jrgibb on 2007-07-05
Hi,

Thanks, I've got Mysql installed (I get the list of commands etc when I type in mysql --help in the terminal). It's ver 14.12 distrib 5.0.38 readline 5.2.

I'm running 7.04 feisty. Have lasted version of Amarok.

I don't think thee's a database created or users, when I type in mysql in the terminal I get the error posed above. 

I get the same when logged in a root.

Do you need any more info? 

J

ps just popping out for 1.5 hours so will get back to this asap :-)

---

### Post by jrgibb on 2007-07-05
Back now . . all help greatfully received.

J

---

### Post by jrgibb on 2007-07-05
I did it myself ;). 

Found this site (below) which got me to the point of installing Mysql, setting up a root password and creating a database. Thereafter Amarok created the database structure, and I'm using MtSQL Administrator to backup etc.

[http://www.yolinux.com/TUTORIALS/LinuxTutorialMySQL.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialMySQL.html)

Oh and you have to use Mysql if you've got any kind of valoume of music (1,000 +) the SQLite just can't cope - as I've now discovered now I see how quick SQL is !

---

### Post by moredhel on 2007-07-05
hmm, that looks good, I will try it later. Also, does anyone know what exaile uses?

---

### Post by walt+walt on 2007-07-07
Hi fans, me too get the very same error. Also, I have followed all of the good ideas in this and other threads. No - absolutly no help in my case. The link from jrgibb wasn't bad, but resulted in a bunch of other error-messages.

Now, is there a working way to run Amarok with another db as mysql? 

And, how are people dealing with mysql in feisty in a productiv manner?

I just hate to switch to another distro just because I can't get mysql running.

Uff, I seem frustrated, but this is the 3rd day I try how-tos and tips out.

But, hope is the last thing who dies -smile-

cheers, walt

---

### Post by The_Major on 2007-07-08
I tried the howto on the amarok wiki but amarok would not connect to the database so I installed the mysql admin gui via synaptic, fired it up and deleted both the amarok database and user recreated both , granted privileges and works!

 I now have amarok working with conky also, bargain!

---

### Post by moredhel on 2007-07-08
hmm, I might try that :)

---

