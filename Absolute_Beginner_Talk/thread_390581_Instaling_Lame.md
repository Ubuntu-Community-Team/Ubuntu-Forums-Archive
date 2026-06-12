---
title: "Instaling Lame"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-03-22
Ooops, didn't get my question asked before I pressed the GO button . . .

I'm installing Lame -- have gotten the source file and applied

./configure
make
make install

Everything seems to go OK with the first two commands, but 'make install' gives me a whole string of the following (and similar) errors. What gives?

------------------------------------------------------------------



Making install in i386
make[2]: Entering directory `/home/leslie/Desktop/lame-3.97/libmp3lame/i386'
make[3]: Entering directory `/home/leslie/Desktop/lame-3.97/libmp3lame/i386'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/leslie/Desktop/lame-3.97/libmp3lame/i386'
make[2]: Leaving directory `/home/leslie/Desktop/lame-3.97/libmp3lame/i386'
make[2]: Entering directory `/home/leslie/Desktop/lame-3.97/libmp3lame'
make[3]: Entering directory `/home/leslie/Desktop/lame-3.97/libmp3lame'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libmp3lame.la' '/usr/local/lib/libmp3lame.la'
/usr/bin/install -c .libs/libmp3lame.so.0.0.0 /usr/local/lib/libmp3lame.so.0.0.0
/usr/bin/install: cannot remove `/usr/local/lib/libmp3lame.so.0.0.0': Permission denied
make[3]: *** [install-libLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/leslie/Desktop/lame-3.97/libmp3lame'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/leslie/Desktop/lame-3.97/libmp3lame'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/leslie/Desktop/lame-3.97/libmp3lame'
make: *** [install-recursive] Error 1

---

### Post by andreas64 on 2007-03-22
Hi,

why don't you install lame via Synaptic. It's in the multiverse repo.

Andreas

---

### Post by lwalper on 2007-03-22
Now that's probably a better idea !!

---

### Post by konst88 on 2007-03-22
It should be:
sudo make install
But a better solution is using checkinstall.

---

