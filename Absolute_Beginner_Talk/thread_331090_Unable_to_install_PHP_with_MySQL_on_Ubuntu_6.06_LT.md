---
title: "Unable to install PHP with MySQL on Ubuntu 6.06 LTS"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by smith.norton on 2007-01-04
I try to install PHP 5.2.0 with MySQL 5.0.27 and Apache 2.2.3

```
$ sudo ./configure --with-mysql=/usr/local/mysql --with-apxs2=/usr/local/apache2/bin/apxs
```.

I get the following error:-

```
checking whether to include mime_magic support... no
checking for MING support... no
checking for mSQL support... no
checking for MSSQL support via FreeTDS... no
checking for MySQL support... yes
checking for specified location of the MySQL UNIX socket... no
checking for MySQL UNIX socket location... no
checking for mysql_close in -lmysqlclient... no
checking for mysql_errno in -lmysqlclient... no
configure: error: Try adding --with-zlib-dir=<DIR>. Please check config.log for more information.

```

Next I try,
```
sudo ./configure --with-mysql=/usr/local/mysql --with-apxs2=/usr/local/apache2/bin/apxs --with-zlib-dir=/usr/lib --includedir=/usr/local/mysql/include
```

Still I get this,

```
checking for MySQL support... yes
checking for specified location of the MySQL UNIX socket... no
checking for MySQL UNIX socket location... no
checking for mysql_close in -lmysqlclient... no
checking for mysql_error in -lmysqlclient... no
configure: error: mysql configure failed. Please check config.log for more information.
```

I find this in the last few lines of config.log

```
collect2: ld returned 1 exit status
configure: failed program was:
#line 58262 "configure"
#include "confdefs.h"
/* Override any gcc2 internal prototype to avoid an error.  */
/* We use char because int might match the return type of a gcc2
    builtin and then its argument prototype would still apply.  */
char mysql_error();

int main() {
mysql_error()
; return 0; }
```

Can anyone please help me out?

---

### Post by oyvindaa on 2007-01-04
Hi there.

If you take a look at [this](http://ubuntuguide.org/wiki/Dapper#Apache_HTTP_Server) guide, you should be able to install php5, mysql and apache2 and make them work together. I've used these instructions myself and it works just perfect. Just follow the instructions from the apache2 install and so forth.

---

### Post by l.tambiah on 2007-01-04
You can also use my guide @ [http://www.ossgeeks.co.uk/?p=15](http://www.ossgeeks.co.uk/?p=15)

---

