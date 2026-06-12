---
title: "installing Apache"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by SpikeyMike on 2007-05-28
Hi, I am trying to install apache on Ubuntu, I know I could have done it from the package manager but I wanted to find out how to do it from the source files. I downloaded the files and unpacked them then typed the following command in a terminal:

[COLOR="Red"]root@MyUbuntu:/home/mikey/httpd-2.0.59# ./configure --prefix=/usr/local/apache2 --enable-module=so[/COLOR]
 
but the following was displayed:

[COLOR="Red"]checking for chosen layout... Apache
checking for working mkdir -p... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1

Configuring Apache Portable Runtime library ...

checking for APR... reconfig
configuring package in srclib/apr now
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
Configuring APR library
Platform: i686-pc-linux-gnulibc1
checking for working mkdir -p... yes
APR Version: 0.9.12
checking for chosen layout... apr
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
configure failed for srclib/apr
[/COLOR]

I think it might be something to do with permissions as I noticed I do not have permission to write to the /usr/local/ directory. If so how do I change the permissions?

Regards

Spikey

---

### Post by taurus on 2007-05-28
You need the build-essential package before you can build anything from source.

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

