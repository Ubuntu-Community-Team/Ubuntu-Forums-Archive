---
title: "Compiling - Error 77"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by OkydOky on 2006-02-23
I was following [this]("http://www.winehq.com/site/download-deb") guide, more specifically "Building the Wine Package from Source using APT"
To Try and Get Wine, I am Using the 64bit version of Ubuntu.

```
$ sudo apt-get --build source wine
Reading package lists... Done
Building dependency tree... Done
Need to get 13.5MB of source archives.
Get:1 http://wine.sourceforge.net source/ wine 0.9.8-winehq-1 (dsc) [1137B]
Get:2 http://wine.sourceforge.net source/ wine 0.9.8-winehq-1 (tar) [13.4MB]
Get:3 http://wine.sourceforge.net source/ wine 0.9.8-winehq-1 (diff) [46.7kB]
Fetched 13.5MB in 1m46s (126kB/s)
dpkg-source: extracting wine in wine-0.9.8-winehq
dpkg-source: unpacking wine_0.9.8-winehq.orig.tar.gz
dpkg-source: applying ./wine_0.9.8-winehq-1.diff.gz
dpkg-buildpackage: source package is wine
dpkg-buildpackage: source version is 0.9.8-winehq-1
dpkg-buildpackage: source changed by Scott Ritchie <scott@open-vote.org>
dpkg-buildpackage: host architecture amd64
 debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/home/thierry/wine-0.9.8-winehq'
make[1]: *** No rule to make target `distclean'.  Stop.
make[1]: Leaving directory `/home/thierry/wine-0.9.8-winehq'
make: [clean] Error 2 (ignored)
#-/usr/bin/make -C documentation clean
dh_clean
 debian/rules build
dh_testdir
# Add here commands to configure the package.
CFLAGS="-Wall -g -O2" ./configure --host=x86_64-linux-gnu --build=x86_64-linux-gnu --prefix=/usr --mandir=\${prefix} /share/man --infodir=\${prefix}/share/info
checking build system type... x86_64-pc-linux-gnu
checking host system type... x86_64-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for x86_64-linux-gnu-gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [config.status] Error 77
Build command 'cd wine-0.9.8-winehq && dpkg-buildpackage -b -uc' failed.
E: Child process failed
```

---

### Post by gord on 2006-02-23
try installing the build-essential package first
```

sudo apt-get install build-essential

```

---

### Post by schenkin on 2006-02-23
Heh, i am having the exact same problem. Build-essential is already installed. Would it help if I posted my config.log file?

---

### Post by schenkin on 2006-02-23
I have tried the following:

$export CC=gcc which i found here: [http://ubuntuforums.org/showthread.php?t=17033]("http://ubuntuforums.org/showthread.php?t=17033")

It got farther after i did this however. Now i am getting the following errors:

../../include/winnls.h:746: warning: &#8216;__stdcall__&#8217; attribute ignored
../../include/winnls.h:747: warning: &#8216;__stdcall__&#8217; attribute ignored
../../include/winnls.h:749: warning: &#8216;__stdcall__&#8217; attribute ignored
../../include/winnls.h:750: warning: &#8216;__stdcall__&#8217; attribute ignored
../../include/winnls.h:751: warning: &#8216;__stdcall__&#8217; attribute ignored
../../include/winnls.h:753: warning: &#8216;__stdcall__&#8217; attribute ignored
../../include/winnls.h:754: warning: &#8216;__stdcall__&#8217; attribute ignored
../../include/winnls.h:756: warning: &#8216;__stdcall__&#8217; attribute ignored
../../include/winnls.h:757: warning: &#8216;__stdcall__&#8217; attribute ignored
../../include/winnls.h:758: warning: &#8216;__stdcall__&#8217; attribute ignored
make[3]: *** [casemap.o] Error 1
make[3]: Leaving directory `/var/log/wine-0.9.8-winehq/libs/unicode'
make[2]: *** [unicode] Error 2
make[2]: Leaving directory `/var/log/wine-0.9.8-winehq/libs'
make[1]: *** [libs] Error 2
make[1]: Leaving directory `/var/log/wine-0.9.8-winehq'
make: *** [build-stamp] Error 2
Build command 'cd wine-0.9.8-winehq && dpkg-buildpackage -b -uc' failed.
E: Child process failed

---

### Post by OkydOky on 2006-02-23
build-essential was already installed.
So did not work.

Anyone else have any Idea... I really would like to get wine to work >.<

---

