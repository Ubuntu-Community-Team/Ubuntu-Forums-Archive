---
title: "Questions about how apt works vs. compiling from source: php5"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by mindstorm23 on 2007-04-23
I'm setting up a web server with Ubuntu (Feisty) that will be used as a testing/development server.  I want to install php5 on it, but I want to make sure that the compile options are the same as the live server that I want this test server to mirror.  The live server is running Red Hat EL4.

I am new to apt, but I am familiar with compiling programs from source.  Ideally, I'd like to just "apt-get install php5" and be done with it.  However, like I stated before, I want the compile options to be the same as my live server, and chances are that apt won't give me what I need as far as that goes.

Having said all that, I'm needing to know my options and how flexible I can be with this.  I'm guessing I can at least do "apt-get build-dep php5" to get most of what I need, and let ./configure tell me what I'm missing.  However, I have a few question still:

[LIST]
[*]If I compile php5 from source, can I still install packages on top of it as if I had apt-get'd it?  Or will I have to recompile? For example, can I "apt-get install libapache2-mod-php5" and expect it to work?
[*]Is there another way to build php5 from source (somehow using apt-get source php?) and be able to edit compile options that might be easier than straight-up source, and still work with apt?  Or even if it doesn't work with apt, is there an easier way?
[/LIST]

I really appreciate any help you can offer.

For the sake of reference, here is the ./configure command pulled straight from phpinfo() on my live server (these are the options I want compiled in):

```
'./configure' '--host=i686-redhat-linux-gnu' '--build=i686-redhat-linux-gnu' '--target=i386-redhat-linux' '--program-prefix=' '--prefix=/usr' '--exec-prefix=/usr' '--bindir=/usr/bin' '--sbindir=/usr/sbin' '--sysconfdir=/etc' '--datadir=/usr/share' '--includedir=/usr/include' '--libdir=/usr/lib' '--libexecdir=/usr/libexec' '--localstatedir=/var' '--sharedstatedir=/usr/com' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--cache-file=../config.cache' '--with-libdir=lib' '--with-config-file-path=/etc' '--with-config-file-scan-dir=/etc/php.d' '--disable-debug' '--with-pic' '--disable-rpath' '--with-pear' '--with-tidy' '--with-exec-dir=/usr/bin' '--with-png-dir=/usr' '--enable-gd-native-ttf' '--without-gdbm' '--with-jpeg-dir=/usr' '--with-openssl' '--with-png' '--with-pcre-regex=/usr' '--with-mime-magic=/etc/httpd/conf/magic' '--with-gd' '--enable-bcmath=shared' '--enable-dba=shared' '--with-db4=/usr' '--with-xmlrpc=shared' '--with-ldap=shared' '--with-mysql' '--with-mysqli=/usr/bin/mysql_config' '--enable-soap=shared' '--enable-fastcgi' '--enable-so=shared' '--with-apxs2=/usr/sbin/apxs' '--with-mssql=/usr/local'
```

Notes: my live server is running Apache 2.0, while my Feisty test server has Apache 2.2.  Also, note that I need MSSQL support, so freetds is one of the dependencies I'll have to grab along the way.

---

### Post by Cypher on 2007-04-23
if you look at the file here:[http://archive.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.2.1-0ubuntu1.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.2.1-0ubuntu1.diff.gz)

This is basically what the maintainer of the libapache2-mod-php5 package has added to the base PHP package and build it. You can also look for the Rules file in there and see the "configure" options that are being given.

Regards

---

### Post by psusi on 2007-04-23
If you build the package ( with say, pbuilder or dpkg-buildpackage ) then install the resulting binary package ( the .deb ) rather than just make install, then related packages are very likely to just install from apt-get just fine as they will see that the first package is installed.  If you just make install, apt doesn't know the package is installed.

---

