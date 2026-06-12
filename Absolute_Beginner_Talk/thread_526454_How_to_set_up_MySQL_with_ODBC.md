---
title: "How to set up MySQL with ODBC"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by wenmark on 2007-08-15
I am a Linux newbie, and have set up a 7.0.4 server with LAMP.
I need to set up an ODBC connection so I can use my windows tools (Navicat and others) to create/manage/update MySQL databases.
I have installed libmyodbc on Ubuntu and mysql-connector-odbc on my windows xp machine, but I cannot connect tothe server.

can anyone help me out?

Thanks
Mark

---

### Post by ukripper on 2007-08-15
are you getting any error message?

---

### Post by PaulHuffman on 2007-10-04
Hey, you can run Navicat on Linux?

---

### Post by Egill Th on 2007-10-04
Hi,

"I need to set up an ODBC connection so I can use my windows tools (Navicat and others) to create/manage/update MySQL databases."

If I were you, I would use PHPMyAdmin.

To get PHPMyAdmin, type this in your terminal:
sudo apt-get install phpmyadmin

to access PHPMyAdmin go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Best regards,
Egill Th

---

### Post by PaulHuffman on 2007-10-16
You can use JDBC to make a connection to Open Office database tables.  I just figured it out: [http://ubuntuforums.org/showthread.php?t=502412]("http://ubuntuforums.org/showthread.php?t=502412")

---

### Post by fleet on 2007-10-18
The JDBC coonetion in OO.org is very flaky. In my experience it crashed every third or forth connection. ODBC is as easy to set up an far more reliable.

---

### Post by PaulHuffman on 2007-10-18
I followed the instructions for an ODBC connection at [https://help.ubuntu.com/community/ODBC]("https://help.ubuntu.com/community/ODBC")

but when I try it with OO I got a message that it can't load the program library libodbc.so.1.  What happened? When I look in /usr/lib/odbc  I find libmyodbc.so but not libodbc.so.1

OK, I figured it out.  I looked at packages in Synaptic PM,  found libodbc++4, that looked close enough, so I installed it.  My ODBC connection in OO still gave me the same message, so I took a chance and made a symbolic link in /usr/lib : ln -s libodbc++.so.4 libodbc.so.1 to fool OO's dialog by in effect naming the new lib with two different names.  Then the OO new database routine let me go ahead and connect to my MySQL database.  The database name I put in my odbc.ini appeared in the dialog, and I new I was there.   I'll drive the JDBC vesrion and the ODBC version for a while and see which one performs better.

---

