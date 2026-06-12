---
title: "Ubuntu and SQL database"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Tubaboy on 2007-05-04
Hi-

I'm trying to get out of the MS nightmare, and would like my next laptop to be Ubuntu- BUT I have to be able to make a database connection with the SQL database on my MS server.

Is this possible?

---

### Post by Cypher on 2007-05-04
What sort of a connection are we talking about here? I assume that SQL server is running on a different machine and allows for remote access?

I don't believe there are any native SQL management software for Linux. You could, howeve, run the Windows version under Wine..

---

### Post by useLinux, on 2007-05-04
How do you mean, like access the database on your MS server? Or litterly transfer data from your laptop to your MS server?

---

### Post by HeavyAl on 2007-05-04
Not sure the exact situation here, but you may be able to use Rekall ([www.rekallrevealed.org](www.rekallrevealed.org)) and the Unix ODBC driver to remotely connect and manipulate your SQL db.

There is also a tool called DBVisualizer ([www.minq.se/products/dbvis/](www.minq.se/products/dbvis/)) that I've heard good things about but never tried myself.

Finally, there are the MySQL tools - they are geared for MySQL but WILL work for MsSQL. They're in the repos.

---

### Post by Tubaboy on 2007-05-04
Thanks- I'm currently using MS Access with an ODBC connection for remote access to the SQL database- it would be great to find someone who's already done it. Anybody out there?

---

### Post by Howler9443 on 2007-05-04
I'm not certain about accessing MS Access via a native Linux driver, but I use [FreeTDS]("http://www.freetds.org/") to access our SQLServer at work.  Its a library that allows access to SQLServer and Sybase style databases.

Its not a GUI, but a library that you can code against to access SQLServer.

[http://www.freetds.org/]("http://www.freetds.org/")

I hope this helps.

---

### Post by Hendrixski on 2007-05-04
If I understand correctly... you want to switch to Linux, but need databases.

Most of the worlds best databases run on Linux.  for example, Oracle (arguably the best commecrcial database) recommends Linux as it's preferred platform.  But that's something like $40,000 per license.

The most popular database in the world is MySQL, and it is beautiful on Linux.  It's on something like half of the worlds internet and small business servers (very famous for being part of the LAMP software stack which is Linux+apache+mySQL+PHP).  Hands down has more users than any other database in the world.

Access is not a very good database.  I used to consult for a wide range of businesses, from small businesses to large ones, and I have never once seen it deployed in the field.  SQL Server however is pretty decent, has some good tools, is widely used and doesn't run on Linux as far as I know.

If you want something to replace access, use the database that you get with your ubuntu.  It's called OpenOffice Base.  It's easier to use than Access, and probably just as small.  If not, again, mySQL is VERY easy to install.  And it'll do everything that SQL Server can.  And you'll probably find more people with mySQL experience than SQL Server experience because after all, it's very popular.

So yes.  Ubuntu and databases = powerful and easy.

---

### Post by compmodder26 on 2007-05-04
I believe the OP needs a client to be able connect to an MsSQL database on a windows server.

---

### Post by Tubaboy on 2007-05-04
Thank you all-

Hendrixci-

I'm not using MS Access for the database, just using it on my laptop to connect and manipulate the SQL database.

Trust me, "If I knew then what I know now", I wouldn't have anything to do with an MS server.

Again, thanks, it looks like there are easy solutions to make this connection on a linux box, I'm going for it....

---

### Post by abadr on 2007-06-16
I run K/Ubuntu and use MSSQL all the time but not using a native application or wine. I simply remotely connect to the MSSQL server using KRDC (Kubuntu) or Terminal Services Client (Ubuntu). These 2 programs support the RDP protocol used by the Windows servers Terminal Services which you need to make sure its running on the windows server. I'm sussefully using those 2 program to connect to windows 2000 server and windows 2003 servers. 

It's amazing how well this works even across the Internet, the servers are in the US and I'm in Egypt. 

Another option is to use VMware player to run a guest operating system (windows in this case) in a window in Ubuntu and install any program you need in that. I use that all the time to run things like dreamweaver.

If you need anymore info let me know.

---

