---
title: "Can OpenOffice.org be used with mysql?"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-07-16
Can OpenOffice.org be used with mysql?

What I mean is can I connect to mysql with OpenOffice and manage, edit, create databases?

If so a howto would be nice.

Thanks.

---

### Post by scrooge_74 on 2007-07-16
Did you check the documentation at openoffice.org?  I seem to remember something to that effect

---

### Post by geek_Man on 2007-07-16
I think there might be, but it was a long process, requiring you to download something, so I gave up.

---

### Post by guysmiley25 on 2007-07-17
Yeah it appears like you can.

If I go into OpenOffice.org, then select New -> Database.. I can then go to select Connect to an existing database, and select mysql. Then I goto next. Then I have to choose either ODBC or JDBC. I do not know what these are.

Thanks for the info so far guys.

---

### Post by scrooge_74 on 2007-07-17
ODBC and JDBC if i am not mistaken,  is the driver for connecting. I know one is better, just dont remember which one I think is ODBC

---

### Post by geek_Man on 2007-07-17
If I remember correctly, I could only use JDBC (has something to do with Java), but like I said, I gave up.

---

### Post by mättu on 2007-08-17
follow instructions in this thread, this worked for me:
[http://ubuntuforums.org/showthread.php?t=122771&highlight=jdbc+HOWTO](http://ubuntuforums.org/showthread.php?t=122771&highlight=jdbc+HOWTO)

basically, i needed to install libmysql-java:
sudo apt-get install libmysql-java

then close all instances of openoffice and retry.

I understand from your posts that you have mysql up and running. If not, the thread above shows how to.

Open dialog for new database in openoffice, then choose mysql. In the next window choose jdbc, in the following enter the name od your database. The server name is "localhost" for local installs.
That's it. If not, feel free to post back.

greets
:m)

---

### Post by PaulHuffman on 2007-10-15
It worked!  I thought I had to write a java class to connect when I read [http://ubuntuforums.org/showthread.php?p=3539844#post3539844]("http://ubuntuforums.org/showthread.php?p=3539844#post3539844") but once I installed the libmysql-java, I just followed along with the instructions in OO and it worked.   Does anyone in the linux world use OBDC, or is it mainly JDBC?

---

