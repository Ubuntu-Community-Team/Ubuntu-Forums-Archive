---
title: "Installing Nagios NDOUtils on Ubuntu 7.10"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by jspencer241 on 2007-12-16
I've finished installing Nagios 3.0b7 on Ubuntu 7.10 as a LAMP. Everything is working as expected.
Now I'm trying to to install NDOUtils 1.4b7. When I ./configure it tells me it cannot find the mysql libraries. Here is the output form the ./configure:

checking for mysql_store_result in -lmysqlclient... no
checking for mysql_connect in -lmysqlclient... no


*** MySQL library could not be located... **************************

You chose to compile NDBXT with MySQL support, but I was unable to
locate the MySQL library on your system.  If the library is
installed,  use the --with-mysql-lib argument to specify the
location of the MySQL library.

NOTE: After you install the necessary libraries on your system:
      1. Make sure /etc/ld.so.conf has an entry for the directory in
         which the MySQL libraries are installed.
      2. Run 'ldconfig' to update the run-time linker options.
      3. Run 'make devclean' in the NDBXT distribution to clean out
         any old references to your previous compile.
      4. Rerun the configure script.

TIP: Try the following....

         ./configure --with-mysql-lib=/usr/lib/mysql

********************************************************************


checking mysql/mysql.h usability... no
checking mysql/mysql.h presence... no
checking for mysql/mysql.h... no


*** MySQL include file could not be located... **********************

You chose to compile NDBXT with MySQL support, but I was unable to
locate <mysql/mysql.h> on your system.  If the include file is
installed, use the --with-mysql-inc argument to specify the location
of the MySQL include file.


Where can I locate the files it's looking for?

---

### Post by hfranco on 2007-12-18
Obvious question but have you tried installing mysql-client?

```
sudo apt-get install mysql-client
```

---

### Post by svalding on 2008-01-25
Seems to be a buggish issue with the new version of mysql. Downgrade to 1.4b6 and it should be ok. Also post up to the [email]nagios-users@lists.sourceforge.net[/email] mailing list for further assistance.

---

### Post by kallek on 2008-01-28
Hi,
I do not know if this is relevant, but it seem like you are missing the /usr/include/mysql/ directory. I had a similar problem trying to compile mYm (Matlab interface to MySQL). 
Installing libmysqlclient15-dev solved the problem.

Kallek

---

### Post by cixelsydego on 2008-07-10
I know that it is not Ubuntu; however, I am installing NDOUTILS on centos5-x86_64.  I ran into the exact same error as described above.

To solve it, I pointed configure directly to my 64bit mysql lib directory, like so:

 ./configure --with-mysql-lib=/usr/lib64/mysql


Everything looks good now.

Cixel

---

