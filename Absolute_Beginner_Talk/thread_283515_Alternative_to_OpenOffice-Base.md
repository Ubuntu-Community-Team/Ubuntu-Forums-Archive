---
title: "Alternative to OpenOffice-Base"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by saphil on 2006-10-24
Hi,
I am looking for an alternative to Open-Office Base
for database design.

OpenOffice Base takes all available cpu cycles to do anything of value, such as editing a table, or even click the tables view when the app opens.  It also crashes in the middle of operations, locking misconfigurations into tables as it goes down.  I would like a local system - fox-pro was my favourite 10 years ago, but on a 486 with win3.11.  I really wish OO didn't have this bug (which I have reported) but it 

Would I be better off, in the long run designing a mysql database - tables, forms and reports.  I can do that, I guess, but I am not intending to put the database in the Internet.  Maybe that would increase my options later, but if it came up I could probably export to mysql later, too.  If I go with local development of a mySql database, what would be the gui of choice to develop forms and tables and whatever?

---

### Post by sonny on 2006-10-24
Well OpenOffice-Base is like Access and like access it's not a great help with large datasets, your best choice would be some sql database, or if you know oracle you can use that. But I wouldn't recommend OO-Base as I wouldn't recommend MS-Access.

---

### Post by saphil on 2006-10-24
Thanks,
So what front-end would you suggest?  Assume we have $0 budget (which is $10 more than we actually have in the budget right now  :) )

I am wanting to be able to develop small-data-set database examples that could be ported or converted to MySql, so starting in Sql would be ok.  The nice thing about (at least the ideal case of) OO-Base would be the speed of developing the tables relationships and forms for demonstration to stake-holders.  At the moment - because of previous experience, I seem to believe that developing an sql database is slower, and maybe harder than developing a local table-top database.  Were that OOBase did not have the bug that slows it down so, I wouldn't be asking at all.  

-Wolf

PS  I don't mind being told.. "RTFM", if you happen to know what that manual is called so I can find it.

---

### Post by marianom on 2006-10-24
You should start directly with MySQL if that's your final goal.

If you really need a front end to create the relations you could try MySQL Workbench:
[http://www.mysql.com/products/tools/workbench/](http://www.mysql.com/products/tools/workbench/)

---

### Post by saphil on 2006-10-24
Thanks, I will woodshed this and see.

-Wolf

---

### Post by mssever on 2006-10-24
I recommend mysql and phpMyAdmin. ```
sudo aptitude install phpmyadmin
``` should get you everything you need. phpMyAdmin has much better functionality than any other front end I've used.

---

### Post by Marsolin on 2006-10-24
There are a lot of [alternatives]("http://linuxappfinder.com/databases/editorsinterfaces") to [OpenOffice.org - Base]("http://linuxappfinder.com/package/openoffice.org-base"). [Kexi]("http://linuxappfinder.com/package/kexi"), [Knoda]("http://linuxappfinder.com/package/knoda"), [Rekall]("http://linuxappfinder.com/package/rekall"), and [Glom]("http://linuxappfinder.com/package/glom") to name a few.

---

### Post by brentoboy on 2006-10-24
be thoughtful of what database you choose if you *ever* and I mean *ever* decide to make a comercial venture out of whatever you are developing.

I dont mean selling the program, even selling the "service" offered by your program, some databases, like kexi, and maybe others have various licensing schemes depending on what you are doing with them.  The Windows version of Kexi isnt freely redistributable.  MySQL cant be redistributed with your software without kicking out a $500 per installation (or open sourcing your program to match their licenseing scheme)

The "free-est" license that I am ware of is SQLite.  (its pretty BSD-ish)

I personally see two kinds of database applications:  1) applications that run inside of a database environment (access, foxpro, oo-base)  and 2) applications which store data in a database.

The primary difference is that the applications that store data can be database specific, and the user interface is written in the language of choice for the programmer.  The "database hosted" applications are written in the language provided by the db environment.

You generally have easier DB access from within the db enviroment, but limited GUI options.  Even though it is convenient to write "applications" inside of db environments, once you step outside that world, you will never go back.  The other way has some learning curve involved, but really isnt that much more involved once you have done it a couple of times.

If you intend to always run on linux, I would recommend using either glade+python or wxPython for your gui, and the SQLite python plugins.  (Unless you are good with C/C++ The more I work on stuff the more I am starting to believe that if its worth doing, its worth designing correctly and implementing in C/C++)

SQLite has a control center.  I have never used the linux version of it.

MySQL has an intersting license scheme, and before you write much code around it (except as a data source for your web-site) I would first read their licensing schemes.

I have discovered over time, that it is not uncommon to take a "home project" and one day make a service out of it that makes money.  You dont want to get there and then discover that the DB you have built your world around doesnt allow that.

One thing that I do is design the tables and queries inside of a db environment and fill it with some fake data that looks like the intended end product.  Once you have it there, you can see that your queries are matching up and returning what you expect.  Then you open up glade, and start making forms for working with your data, then you create your DB in a "real" database format (like MySQL, Postgre... SQLite if it is a relitivly simple app) and then use python to pull data from the db and put it on the form.

Once you get there you are hooked.

-b

---

### Post by mssever on 2006-10-24
The free version of MySQL is licensed onder the GPL, so it isn't necessarily a problem for commercial ventures. Basically, if you want to distribute your closed-source commercial product along with mysql, you could have problems. If you say that your product requires mysql and either distribute mysql in accordance with the GPL or direct your users to install mysql, then you should be OK. Or, if you set up a central database server and your commercial software merely connects to it, you should be fine. But I'm not a lawyer.

The only thing that the GPL restricts is how you *redistribute* the software--not how you *use* it.

---

### Post by marianom on 2006-10-24
If your requirement matches the hardware constraints the soft has, Oracle XE is free too. See [http://www.oracle.com/technology/products/database/xe/index.html](http://www.oracle.com/technology/products/database/xe/index.html)

---

### Post by saphil on 2007-01-14
Minor update.  
Thanks for all your help.  I have been playing around with all the new ideas. 

 I did find out last week that my major problem with OOBase was that it was not connected well to the /usr/.../java for some reason.  I was updating java for some other purpose and OOBase came up with an error message (1st ever) saying the path to java was wrong.  Redirecting the path to the new java made OOBase much more zippy.  No crashes since then.

I am looking at mySQL as a base for my apps now, because everything I am doing is web-based and almost every commercial host has mySQL as a server component.  (Won't have to distribute it with the app unless I want to)  

Almost everything I do is connected to some open source app.  I do commercial consulting but give away the base software, Drupal, Centris, OpenExchange, and so on.

---

