---
title: "PHP beginners install"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by Llwyd on 2006-07-31
Hi,

I have installed ubuntu and would like to install php (LAMP if that is correct).  I have search for this in the applicaitons but not found it can anyone point me in the right direction.

Regards
Bach.

---

### Post by az on 2006-07-31
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

Also see:
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by indytim on 2006-07-31
For Apache and PHP see

[http://doc.gwos.org/index.php/Latest_Apache_and_PHP]("http://doc.gwos.org/index.php/Latest_Apache_and_PHP")

There used to be a consolidated guide to the entire LAMP package.  I'm at work right now and don't have my usual compliment of bookmarks.  Perhaps someone else from the collective could chime in with a link to the old guide.  In the meatime, the above should get you up and running.  Recommend that you pay attention to the section dealing with PHP4 vs PHP5.

Good Luck,

IndyTim

---

### Post by indytim on 2006-07-31
Use Azz's links... those were the one's I was referring to.  We must have been simul-posting :D 

IndyTim

---

### Post by Llwyd on 2006-07-31
Thank you both for your replies.

I have run the installations listed in the link you mentioned, using "Synaptic Package Manager".

Looking at the [Apache and PHP]("http://doc.gwos.org/index.php/Latest_Apache_and_PHP") guide it mentions configuration of the packages - **Making PHP work in Apache**, I am unable to find the folders for the configuration.

Any help!

Regards

---

### Post by az on 2006-07-31
> **Llwyd said:**
> Thank you both for your replies.

I have run the installations listed in the link you mentioned, using "Synaptic Package Manager".

Looking at the [Apache and PHP]("http://doc.gwos.org/index.php/Latest_Apache_and_PHP") guide it mentions configuration of the packages - **Making PHP work in Apache**, I am unable to find the folders for the configuration.

Any help!

Regards

That guide if not for Dapper.

Use the Dapper packages and everything is preconfigured.  All you need to do is set a mysql-root password.

---

### Post by Llwyd on 2006-08-01
> **azz said:**
> All you need to do is set a mysql-root password.

Thanks.

---

