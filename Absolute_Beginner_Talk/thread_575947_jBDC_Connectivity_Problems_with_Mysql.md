---
title: "jBDC Connectivity Problems with Mysql"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by fleet on 2007-10-14
I raised this earlier but no response. 

What can I try with 

*Error During Query: Unexpected Exception java.io.char.conversion Exception Message Given: Null. *

When trying jDBC through an OO.org data source with the mysql 5.1.5 connector.

Just can'get this to work. 

Any ideas?

---

### Post by Irihapeti on 2007-10-14
I seem to recall reading somewhere on the OO forums that the JDBC connection is not the most reliable. The ODBC is considered to be better.

I use the ODBC connector to access MySQL databases through OO. 

```
sudo apt-get install libmyodbc
```
installs the package.

Making the connection between OO and MySQL is set out in [http://www.unixodbc.org/doc/OOoMySQL9.pdf](http://www.unixodbc.org/doc/OOoMySQL9.pdf) It's written for OO version 1, but works in 2.2.1 (which is what I'm using) as well. 

I had to change one entry in /etc/odbcinst.ini. In the instructions, it's given as

Driver    = /usr/lib/libmyodbc.so

In Ubuntu, you need to change it to

Driver    = /usr/lib/odbc/libmyodbc.so

or it won't work.

Hope this is of some help.

Irihapeti

---

### Post by fleet on 2007-10-17
Thanks that was like so easy. 

You know I always struggled with the JDBC connector on other installs. Basically it was almost unworkable. This seems so much more solid.:)

---

### Post by Irihapeti on 2007-10-17
You're very welcome.

Irihapeti

---

