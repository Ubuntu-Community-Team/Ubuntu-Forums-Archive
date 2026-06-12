---
title: "PHP with MySQL support problem"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by maz00 on 2007-12-11
Hi all,

I'm trying to configure Ubuntu for the first time (and haven't touched *nix for 3 years now) and surprise, I'm running into problems

I've install mysql using apt-get install mysql (which works)
I've downloaded the source for apache2 and installed it (works)
I've downloaded the source for php and installed. It worked except no mysql support. So I went back and now I'm trying to add mysql to it using --with-mysql= however, it return this error


./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql=/usr/

configure: error: Cannot find MySQL header files under yes.
Note that the MySQL client library is not bundled anymore!

I've tried everything and still no go. This is what I have installed for mysql
ii libdbd-mysql-per 4.004-2 A Perl5 database interface to the MySQL database
un libmysqlclient15 <none> (no description available)
ii libmysqlclient15 5.0.45-1ubuntu3 MySQL database client library
un mysql-client <none> (no description available)
ii mysql-client-5.0 5.0.45-1ubuntu3 MySQL database client binaries
ii mysql-common 5.0.45-1ubuntu3 MySQL database common files
un mysql-doc-5.0 <none> (no description available)
ii mysql-server 5.0.45-1ubuntu3 MySQL database server (meta package depending on
ii mysql-server-5.0 5.0.45-1ubuntu3 MySQL database server binaries
un virtual-mysql-cl <none> (no description available)
un virtual-mysql-se <none> (no description available)


Any pointers here? what am I missing?

BTW, some sites say search for 'find / -name mysql.h' and that file doesn't exist on my computer at all.

Thx
Maz

---

### Post by matthewcraig on 2007-12-11
Maz, sorry you are having a problem.  Didn't I see your question two months ago about an "apt-get install" problem?

---

### Post by LaRoza on 2007-12-11
The best way to do this, is with ```
sudo tasksel
```. There are other packages that are needed, but since the above command can get them all, I won't enumerate them.

---

### Post by maz00 on 2007-12-11
> **matthewcraig said:**
> Maz, sorry you are having a problem.  Didn't I see your question two months ago about an "apt-get install" problem?

haha you did.. I started playing with Ubunto and before getting too far, I got a side job offer that I had to take care of and now I'm free again. So I thought I should continue with Ubuntu. BTW, my area of expertise this past 3 years has been with ASP.NET and MSSQL (my current job). Sometimes I miss *nix and like to update myself.  

Maz.

---

