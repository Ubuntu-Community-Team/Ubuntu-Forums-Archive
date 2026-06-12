---
title: "mysqli for ubunto serve 7.10"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by NOgbourne on 2007-12-11
Hi,
a _very_ new user making quite good progress but I need to use mysqli for various projects.  There seems to be a package for use with 'dapper'  and 'edgy' but not for 'gutsy' which I take to be the version I am using - 7.10.  Yes?

So the question is, can I use the 'Edgy' package (for example) and install it on said 'gutsy'?   Is that possible?  I can't seem to find a definite answer to that.

If not, what alternatives do i have?

Or have I missed something and it is already there.  There is some reference to mysqli in the php config file.  Puzzled.
Regards

Nick

---

### Post by FakeOutdoorsman on 2007-12-12
I don't know if this is what you're looking for, but the package **php5-mysql** summary says that it contains a mysqli module:

*It includes the generic "mysql" module which can be used to connect to all versions of MySQL, an improved "mysqli" module for MySQL version 4.1 or later.*

---

### Post by NOgbourne on 2007-12-12
Yes, looks like the go - now I have to get it to run - preumably bu modifying the php config file.

Thanks

---

### Post by ldsudduth on 2007-12-12
You're using Ubuntu Server Version? If you are, then when you install, it gives you an option for LAMP--Linux, Apache, MySQL, PHP. 
 
If you're using Ubuntu Desktop, MySQL 5 is in the repositories. Use Synaptic and do a search on MySQL. It will also give you the GUI tools and everything else. I would also suggest downloading phpmyadmin and apache. 
 
I have LAMP installed on my desktop, and I did it all from the repositories.

---

### Post by NOgbourne on 2007-12-12
As I said  - a very new user.  Must have missed (and didn't know what the acronym meant at that time - thanks for that) LAMP.  Yes, running the server version.  Have since installed mySQL OK and now, I think, PHP.  I am about to try and find the php extensions to add to the php config file.

Thanks for the note

Nick

---

### Post by NOgbourne on 2007-12-12
Just as a wrap up, for anyone else looking for mysql or mysqli. 

The package is php5-mysql.  After installing it, you need to edit the php.ini file that is under /etc/php5/apache2

Find the section about extensions  and add these two lines.

[FONT="Microsoft Sans Serif"]
extension=mysql.so
extension=mysqli.so[/FONT]


Then restart apache and phpinfo should now show mysql and mysql aas laoded.

Nick

---

### Post by zebog13 on 2008-03-03
Thanks for the wrap up, exactly what I needed.

---

