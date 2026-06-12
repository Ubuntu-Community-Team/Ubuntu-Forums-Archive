---
title: "installing with wget command"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by coubury on 2008-03-02
ok im downloading openSSL 

coubury@coubury-desktop:~$ wget [http://www.openssl.org/source/openssl-fips-1.1.2.tar.gz](http://www.openssl.org/source/openssl-fips-1.1.2.tar.gz)
--01:25:29--  [http://www.openssl.org/source/openssl-fips-1.1.2.tar.gz](http://www.openssl.org/source/openssl-fips-1.1.2.tar.gz)
           => `openssl-fips-1.1.2.tar.gz'
Resolving [www.openssl.org](www.openssl.org)... 195.30.6.166
Connecting to www.openssl.org|195.30.6.166|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,269,831 (3.1M) [application/x-tar]

100%[====================================>] 3,269,831     39.20K/s    ETA 00:00

01:26:51 (40.82 KB/s) - `openssl-fips-1.1.2.tar.gz' saved [3269831/3269831]

coubury@coubury-desktop:~$

so thats saved what commands do i use to install it then?

---

### Post by owbizi on 2008-03-02
First, extract it:
$ tar -vzxf openssl-fips-1.1.2.tar.gz

Then, go to the folder extracted:
$ cd openssl-fips-1.1.2

Configure (generally, it's ./configure, or ./Configure, but here no), make and then, finally, install it:
$ ./config
$ make
$ sudo make install

And it's done! :)

---

