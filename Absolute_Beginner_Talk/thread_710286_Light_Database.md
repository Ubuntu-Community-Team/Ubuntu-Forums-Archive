---
title: "Light Database"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Sleestack on 2008-02-28
I'm looking for a "light" database solution so I can develop a small contact database management solution for personal use. I've looked into using Open Office Base but it's a bit unstable and getting data in and out seems to be a hassle. I do like the easy way I can create forms with Base, though. I've also considered MySQL, PHP and LAMP, but the prospect of running a web server at all times doesn't appeal to me. 

Does anyone have another solution similar to Base, along the lines of MS-Access that's an "all-in-one" database solution? Forms and GUI are a big requirement, running cross-platform would be great. Thanks.

---

### Post by hyper_ch on 2008-02-28
on most databases you'll have to "program" forms and guis yourself. maybe you finde a gui for SQLite

---

### Post by justleen on 2008-02-28
Or maybe the OpenOffice Dbase?  (since you mention MS-Access)

---

### Post by Sleestack on 2008-02-28
I did mention I tried Open Office Base, and it it would meet all my requirements except as I said, it's a bit unstable and getting data in or out requires a hack, or going to the HSQLDB window and exporting from native SQL. I'm not all that comfortable with SQL yet to be proficient at that.

---

### Post by Oldsoldier2003 on 2008-02-28
> **Sleestack said:**
> I did mention I tried Open Office Base, and it it would meet all my requirements except as I said, it's a bit unstable and getting data in or out requires a hack, or going to the HSQLDB window and exporting from native SQL. I'm not all that comfortable with SQL yet to be proficient at that.
Well SQLite or MYSQL would be the best choices on Ubuntu in my opinion. though they will take some learning you'll be well served and most of all you'll be using something not likely to disappear anytime soon. Plus there are tons of available resources to help you learn and people willing to help you muddle through the code if you get stuck.

---

### Post by justleen on 2008-02-28
> **Sleestack said:**
> I did mention I tried Open Office Base, and it it would meet all my requirements except as I said, it's a bit unstable and getting data in or out requires a hack, or going to the HSQLDB window and exporting from native SQL. I'm not all that comfortable with SQL yet to be proficient at that.

My terrible bad!  sorry..:redface:

---

### Post by stevescripts on 2008-02-28
Plus 1 -> SQLite

SQLite databases are very cross-platform.

Steve
(who might even be convinced to script a GUI...  ;) )

---

### Post by Sleestack on 2008-02-28
Thanks for everyone's replies. 

If I use SQLite, will I also need to run a web server if I go the PHP route? 

One of the nice things about HSQLDB (the database engine for the Open Office Base application) is it has a "mini" built-in, purpose-built web server that seems pretty efficient.

---

### Post by stevescripts on 2008-02-28
> **Sleestack said:**
> Thanks for everyone's replies. 

If I use SQLite, will I also need to run a web server if I go the PHP route? 



?  I was under the impression this was for a personal application.

Running/using SQLite does not require a web server.

Lots of scripting language bindings available, along with
C/C++

Steve

---

### Post by Sleestack on 2008-03-05
> **stevescripts said:**
> ?  I was under the impression this was for a personal application.


Yes, this is for a personal application but maybe I'm reaching the end of my understanding here. I'm envisioning creating web forms using HTML and PHP on top of a database. Is a web server needed in this case, or can I hit against the database directly without a web server as intermediary?

---

