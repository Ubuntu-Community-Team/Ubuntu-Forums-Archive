---
title: "How do I install MySQL database?"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by bwallum on 2008-03-21
Hello

I want to install a useable database. the HSQL db in openoffice gives me problems and is no longer being actively developed. 

I want to create tables, queries, forms and reports preferably using a nice n easy gui interface. I can do this with Access. However I am striving to get out of MS. Lets hope the thought police don't arrest me for starting a run but MS has peaked and we are now watching the decline.

MySQL seems to be well regarded. However I am not offered the core db through Ubuntu. I get a few management guis and the like but nothing like Access.

The db is to be run on a stand alone machine initially. i am not looking for a server version (yet).

Can anybody help on this please?

---

### Post by OffAxis on 2008-03-21
Try kexi. You can use it as a standalone or as a frontend to your mysql database.
[http://www.kexi-project.org/](http://www.kexi-project.org/)

It's in the repositories.

```
sudo apt-get install kexi
```

and if you do go that route you might want to install the mdb drivers to migrate existing access stuff over (I've never used them myself so I don't know how well they translate databases over)
```
sudo apt-get install kexi-mdb-driver
sudo apt-get install kexi-mdb-plugin
```

---

### Post by OffAxis on 2008-03-21
you also might like this:
[http://www.fabforce.net/dbdesigner4/](http://www.fabforce.net/dbdesigner4/)

---

### Post by bwallum on 2008-03-23
Unfortunately this project seems closed

> Due to several attacks against the DBDesigner4 forum it has now been closed down.
We simply cannot understand the sick motivation of people to attack Open Source projects.
So please understand that we will not provide any support from now on.

We will continue to host the DBD4 download till the release of the MySQL Workbench,
its successor application that will be an official MySQL product. Then this project will rest in peace.

---

### Post by bwallum on 2008-03-23
Not too sure I want to go down the 'k' route. I just want to know how to run MySQL. Am I not understanding something? I thought I could get a version of MySQL that would run as a standalone db on my desktop machine. Is this a misunderstanding on my part?

Thanks for your response, Bob

---

### Post by kaivalagi on 2008-03-23
To get mysql installed just install 'mysql-server-5' and all it's dependencies through synaptic.

If you want to administer it install 'mysql-admin'. If you want to run queries install 'mysql-query-browser'

There are alternative development frontends to mysql, and it really comes down to personal choice. 

Sqlite may however be what your after, it is a slimmer, less resource hungry database which is being adopted more and more for applications of late. I have not used it myself but it may be worth investigating. I do not know what development frontends are available for it.

As for tools to handle forms and reports, mysql doesn't come with any like this as far as I am aware. The only thing I really know about is the use of apache and php for this type of thing, probably overkill for what you're after!!

---

### Post by bwallum on 2008-03-23
Thanks, I found the magic command (I just love the power of these commands! It makes you really want to learn more.)

```
sudo apt-get install mysql-server
```

I'll follow up on your client/server/admin advice. You have really been helpful and given me an insight into the topography (if thats the right word)

---

### Post by kaivalagi on 2008-03-23
As I develop with a couple of languages I tend to use Eclipse in linux to get things done, as if setup right it is a one stop shop for development. You can set it up to provide support for Java, PHP, Python and MySQL for example

There are so many plugins for Eclipse you will probably find something that suits your needs, but it may take some searching. It also may be a bit overkill if you're used to using Access...but if you're planning on having a client / server type arrangement then this is probably a better way to go :)

Good luck and post back anything you find! If there is a simpler solution to what I've hinted at above, that is not dependent on kde or gtk, I'd love to know about it.

---

### Post by The Cog on 2008-03-23
You should know that msql is just a server, although it comes with a  basic command-line interface to allow administration.
You will probably want to install mysql-admin and mysql-query-browser to give some GUI access to the database.
OpenOffice and kexi provide a fuller "application"-like access. I'm sure there are also others.

---

### Post by bwallum on 2008-03-24
Is it ok to run kexi on a plain Ubuntu Gutsy?

OTOH I now have mysql installed. I thought I would try open office Base frontend. However I need to tell it where an existing db is. How do I create a new mysql db? I have mysql-admin and mysql-query-browser installed. I just can't work out how to create a db in mysql.

I understand that mysql is a server and that I can use my desktop machine as the 'server' machine. I then need to connect to the db with the front end. Beyond that I'm still struggling a bit. I really would like to get mysql going if it is a robust industrial db. I work in IT sometimes and would like to find out more.

Thanks for all your help

---

### Post by kaivalagi on 2008-03-24
Use mysql-admin to create a database and it's security settings etc. I had a quick look at OO Base and it can connect to mysql, beyond that though I know no more than you. I have never used OO Base...

Do some searching online for mysql help, there is plenty out there. The first steps should be relatively easy, it's just a case of getting your head round the details.

I did find this pdf for OO 1.0, a bit out of date but it should get you on the right track: [OpenOffice.org 1.0, ODBC, and MySQL 'How-to' by John McCreesh, April 2003]("http://www.unixodbc.org/doc/OOoMySQL9.pdf")
I found the link on this webpage in case you want to read more: [http://dev.mysql.com/tech-resources/articles/]("http://dev.mysql.com/tech-resources/articles/")

Good luck

---

