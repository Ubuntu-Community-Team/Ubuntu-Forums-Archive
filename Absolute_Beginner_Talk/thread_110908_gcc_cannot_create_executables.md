---
title: "gcc cannot create executables"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by Timokl on 2006-01-01
I try to install Wine from the source as described in [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb).

I installed gcc in advance with

```
sudo apt-get install build-essentials
```

I downloaded all the relevant files with

```
apt-get build-dep wine
apt-get --build source wine
```

which got interrupted once. But finally, I managed to get everything. But afte downloading the compiling failed:

```
dpkg-source: extracting wine in wine-0.9.4-winehq
dpkg-source: unpacking wine_0.9.4-winehq.orig.tar.gz
dpkg-source: applying ./wine_0.9.4-winehq-1.diff.gz
dpkg-buildpackage: source package is wine
dpkg-buildpackage: source version is 0.9.4-winehq-1
dpkg-buildpackage: source changed by Scott Ritchie <scott@open-vote.org>
dpkg-buildpackage: host architecture amd64
 debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Gehe in Verzeichnis »/home/timo/wine-0.9.4-winehq«
make[1]: *** Keine Regel, um »distclean« zu erstellen.  Schluss.
make[1]: Verlasse Verzeichnis »/home/timo/wine-0.9.4-winehq«
make: [clean] Fehler 2 (ignoriert)
#-/usr/bin/make -C documentation clean
dh_clean
 debian/rules build
dh_testdir
# Add here commands to configure the package.
CFLAGS="-Wall -g -O2" ./configure --host=x86_64-linux-gnu --build=x86_64-linux-gnu --prefix=/usr --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info
checking build system type... x86_64-pc-linux-gnu
checking host system type... x86_64-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for x86_64-linux-gnu-gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [config.status] Fehler 77
Build-Befehl »cd wine-0.9.4-winehq && dpkg-buildpackage -b -uc« fehlgeschlagen.E: Kindprozess fehlgeschlagen
```

As you have seen, I run Ubuntu on an AMD64 cpu. What went wrong? How can I resolve that problem?

**Happy New Year!**

---

### Post by Jimmey on 2006-01-17
Yeah, I had the same problem. God knows how I fixed it, but:

I removed gcc (```
sudo apt-get remove gcc
```), and g++, installed them both again, then did the apt-get build-essential. 

Also, try 
```
sudo apt-get -f install
```
```
sudo apt-get update
```

---

### Post by christhemonkey on 2006-01-17
can you not just get wine through the repositories in synaptic?

---

