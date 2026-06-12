---
title: "My first mgetty installation-should I have gone a different way?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by rustyDusty on 2008-02-07
I found an mgetty download from
[http://linux.softpedia.com/progDownload/mgetty-plus-sendfax-Download-263.html](http://linux.softpedia.com/progDownload/mgetty-plus-sendfax-Download-263.html)
that has all the needed files for smooth installation.

I untarred the package.
I am following instructions and I got far enough to change the policy.h-dist file.

Instructions said :
> Then edit "Makefile" to set CC=, CCFLAGS=, INSTALL= and the various 
xxxDIR= (LIB/MAN/BIN/SBINDIR/CONFDIR) to fit your system.

I don't think I needed to make many changes in the Makefile because all the folder links seemed accurate to my system
ex from the Makefile. ```
prefix=/usr/local 
```  meaning anything that says "prefix" points to my usr/local folder like:
```
SBINDIR=$(prefix)/sbin
```

Right?

Ok, so in my terminal I cd'd to the mgetty folder and I did the "make"command. 

My terminal started to scroll a list of data .
```
buc@buc-desktop:~$ cd /home/buc
buc@buc-desktop:~$ cd /home/buc/mgetty-1.1.36
buc@buc-desktop:~/mgetty-1.1.36$ make
gcc -O2 -Wall -pipe -DVARRUNDIR=\"/var/run\" -c mgetty.c
gcc -O2 -Wall -pipe   -c -o logfile.o logfile.c
gcc -O2 -Wall -pipe   -c -o do_chat.o do_chat.c
gcc -O2 -Wall -pipe   -c -o locks.o locks.c
gcc -O2 -Wall -pipe   -c -o utmp.o utmp.c
utmp.c: In function &#8216;make_utmp_wtmp&#8217;:
utmp.c:113: warning: unused variable &#8216;fp&#8217;
utmp.c:112: warning: unused variable &#8216;st&#8217;
gcc -O2 -Wall -pipe   -c -o logname.o logname.c
gcc -O2 -Wall -pipe -DCONFDIR=\"/usr/local/etc/mgetty+sendfax\" -c login.c
gcc -O2 -Wall -pipe   -c -o mg_m_init.o mg_m_init.c
gcc -O2 -Wall -pipe   -c -o modem.o modem.c
gcc -O2 -Wall -pipe   -c -o faxrec.o faxrec.c
gcc -O2 -Wall -pipe   -c -o ring.o ring.c
gcc -O2 -Wall -pipe   -c -o faxlib.o faxlib.c
gcc -O2 -Wall -pipe   -c -o faxsend.o faxsend.c
faxsend.c: In function &#8216;fax_send_page&#8217;:
faxsend.c:214: warning: implicit declaration of function &#8216;strcmp&#8217;
faxsend.c: In function &#8216;fax_send_ppm&#8217;:
faxsend.c:381: warning: implicit declaration of function &#8216;strncmp&#8217;
gcc -O2 -Wall -pipe   -c -o faxrecp.o faxrecp.c
gcc -O2 -Wall -pipe   -c -o class1.o class1.c
gcc -O2 -Wall -pipe   -c -o class1lib.o class1lib.c
gcc -O2 -Wall -pipe   -c -o faxhng.o faxhng.c
gcc -O2 -Wall -pipe   -c -o hyla_nsf.o hyla_nsf.c
gcc -O2 -Wall -pipe   -c -o g3file.o g3file.c
g3file.c: In function &#8216;g3_open_read&#8217;:
g3file.c:103: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217; differ in signedness
g3file.c:103: warning: pointer targets in passing argument 1 of &#8216;__builtin_strcmp&#8217; differ in signedness
g3file.c:103: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217; differ in signedness
g3file.c:103: warning: pointer targets in passing argument 1 of &#8216;__builtin_strcmp&#8217; differ in signedness
g3file.c:103: warning: pointer targets in passing argument 1 of &#8216;__builtin_strcmp&#8217; differ in signedness
g3file.c:103: warning: pointer targets in passing argument 1 of &#8216;__builtin_strcmp&#8217; differ in signedness
g3file.c: In function &#8216;g3_send_file&#8217;:
g3file.c:208: warning: pointer targets in passing argument 1 of &#8216;in_func&#8217; differ in signedness
g3file.c:250: warning: pointer targets in passing argument 1 of &#8216;in_func&#8217; differ in signedness
gcc -O2 -Wall -pipe   -c -o io.o io.c
gcc -O2 -Wall -pipe   -c -o gettydefs.o gettydefs.c
gcc -O2 -Wall -pipe   -c -o tio.o tio.c
gcc -O2 -Wall -pipe -DCONFDIR=\"/usr/local/etc/mgetty+sendfax\" -c cnd.c
gcc -O2 -Wall -pipe   -c -o getdisk.o getdisk.c
gcc -O2 -Wall -pipe   -c -o goodies.o goodies.c
gcc -O2 -Wall -pipe   -c -o config.o config.c
gcc -O2 -Wall -pipe -DFAX_SPOOL_IN=\"/var/spool/fax/incoming\" \
                -DCONFDIR=\"/usr/local/etc/mgetty+sendfax\" -c conf_mg.c
gcc -O2 -Wall -pipe   -c -o do_stat.o do_stat.c
gcc -o mgetty mgetty.o logfile.o do_chat.o locks.o utmp.o logname.o login.o mg_m_init.o modem.o faxrec.o ring.o faxlib.o faxsend.o faxrecp.o class1.o class1lib.o faxhng.o hyla_nsf.o g3file.o io.o gettydefs.o tio.o cnd.o getdisk.o goodies.o config.o conf_mg.o do_stat.o  
logfile.o: In function `lprintf':
logfile.c:(.text+0x1b8): warning: `sys_errlist' is deprecated; use `strerror' or `strerror_r' instead
logfile.c:(.text+0x1af): warning: `sys_nerr' is deprecated; use `strerror' or `strerror_r' instead
gcc -O2 -Wall -pipe   -c -o sendfax.o sendfax.c
gcc -O2 -Wall -pipe -DCONFDIR=\"/usr/local/etc/mgetty+sendfax\" -c conf_sf.c
gcc -o sendfax sendfax.o logfile.o locks.o modem.o faxlib.o faxsend.o faxrecp.o class1.o class1lib.o faxhng.o hyla_nsf.o g3file.o io.o tio.o getdisk.o config.o conf_sf.o goodies.o  
logfile.o: In function `lprintf':
logfile.c:(.text+0x1b8): warning: `sys_errlist' is deprecated; use `strerror' or `strerror_r' instead
logfile.c:(.text+0x1af): warning: `sys_nerr' is deprecated; use `strerror' or `strerror_r' instead
gcc -O2 -Wall -pipe -o newslock compat/newslock.c
gcc -O2 -Wall -pipe -DBINDIR=\"/usr/local/bin\" -DSBINDIR=\"/usr/local/sbin\" \
                -DLIBDIR=\"/usr/local/lib/mgetty+sendfax\" \
                -DCONFDIR=\"/usr/local/etc/mgetty+sendfax\" \
                -DFAX_SPOOL=\"/var/spool/fax\" \
                -DFAX_SPOOL_IN=\"/var/spool/fax/incoming\" \
                -DFAX_SPOOL_OUT=\"/var/spool/fax/outgoing\" \
                -DFAX_OUT_USER=\"fax\" \
                -DVARRUNDIR=\"/var/run\" \
                -DAWK=\"awk\" \
                -DPERL=\""/usr/bin/perl -w"\" -DTKPERL=\"/usr/bin/tkperl\" \
                -DECHO=\""echo"\" \
                -DSHELL=\"/bin/sh\" \
                -DSHELL_TRAP_POSIX=1 \
        -o mksed mksed.c
./mksed >sedscript
chmod +x sedscript
cd g3 ;    make "CC=gcc" "CFLAGS=-O2 -Wall -pipe -I.." "LDFLAGS=" "LIBS=" all
make[1]: Entering directory `/home/buc/mgetty-1.1.36/g3'
gcc -O2 -Wall -pipe -I..   -c -o pbm2g3.o pbm2g3.c
gcc -O2 -Wall -pipe -I..   -c -o g3.o g3.c
gcc -O2 -Wall -pipe -I..   -c -o run_tbl.o run_tbl.c
gcc -O2 -Wall -pipe -I..  -o pbm2g3 pbm2g3.o g3.o run_tbl.o 
gcc -O2 -Wall -pipe -I..   -c -o g3cat.o g3cat.c
gcc -O2 -Wall -pipe -I..  -o g3cat g3cat.o g3.o 
gcc -O2 -Wall -pipe -I..   -c -o g32pbm.o g32pbm.c
gcc -O2 -Wall -pipe -I..  -o g32pbm g32pbm.o g3.o 
gcc -O2 -Wall -pipe -I..   -c -o sff2g3.o sff2g3.c
gcc -O2 -Wall -pipe -I..  -o sff2g3 sff2g3.o g3.o 
make[1]: Leaving directory `/home/buc/mgetty-1.1.36/g3'
cd tools ; make "CC=gcc" "CFLAGS=-O2 -Wall -pipe -I.." "LDFLAGS=" "LIBS=" all
make[1]: Entering directory `/home/buc/mgetty-1.1.36/tools'
../sedscript <kvg.in >kvg
../sedscript <cutbl.in >cutbl
gcc -O2 -Wall -pipe -I.. -c -o ltest.o ltest.c
gcc -O2 -Wall -pipe -I.. -o ltest  ltest.o ../tio.o ../io.o 
gcc -O2 -Wall -pipe -I.. -c -o mid.o mid.c
gcc -O2 -Wall -pipe -I.. -o mid  mid.o ../tio.o \
                ../io.o ../locks.o 
gcc -O2 -Wall -pipe -I.. -c -o microcom.o microcom.c
gcc -O2 -Wall -pipe -I.. -o microcom  microcom.o ../tio.o \
                ../io.o ../locks.o 
make[1]: Leaving directory `/home/buc/mgetty-1.1.36/tools'
cd fax ;   make "CC=gcc" "CFLAGS=-O2 -Wall -pipe -I.." "LDFLAGS=" "LIBS=" "FAX_SPOOL_OUT=/var/spool/fax/outgoing" "FAX_OUT_USER=fax" "CONFDIR=/usr/local/etc/mgetty+sendfax" all
make[1]: Entering directory `/home/buc/mgetty-1.1.36/fax'
../sedscript <faxspool.in >faxspool
../sedscript <faxrunq.in >faxrunq
../sedscript <faxq.in >faxq
../sedscript <faxrm.in >faxrm
../sedscript <faxrunqd.in >faxrunqd
../sedscript <faxheader.in >faxheader
gcc -O2 -Wall -pipe -I.. -DFAX_SPOOL_OUT=\"/var/spool/fax/outgoing\" \
                -DFAX_OUT_USER=\"fax\" \
                -DFAX_ALLOW=\"/usr/local/etc/mgetty+sendfax/fax.allow\" \
                -DFAX_DENY=\"/usr/local/etc/mgetty+sendfax/fax.deny\" \
                -c faxq-helper.c
gcc -O2 -Wall -pipe -I.. -o faxq-helper faxq-helper.o
make[1]: Leaving directory `/home/buc/mgetty-1.1.36/fax'
make[1]: Entering directory `/home/buc/mgetty-1.1.36'
make[1]: `mgetty' is up to date.
make[1]: Leaving directory `/home/buc/mgetty-1.1.36'
cd callback ; make "CC=gcc" "CFLAGS=-O2 -Wall -pipe -I.." "LDFLAGS=" "CONFDIR=/usr/local/etc/mgetty+sendfax" "VARRUNDIR=/var/run" "LIBS=" all
make[1]: Entering directory `/home/buc/mgetty-1.1.36/callback'
gcc -O2 -Wall -pipe -I.. -DVARRUNDIR=\"/var/run\" -c callback.c
gcc -O2 -Wall -pipe -I.. -DCONFDIR=\"/usr/local/etc/mgetty+sendfax\" -c conf_cb.c
gcc -O2 -Wall -pipe -I..  -o callback callback.o conf_cb.o ../config.o ../logfile.o ../do_chat.o ../modem.o ../locks.o ../tio.o ../io.o ../goodies.o 
../logfile.o: In function `lprintf':
logfile.c:(.text+0x1b8): warning: `sys_errlist' is deprecated; use `strerror' or `strerror_r' instead
logfile.c:(.text+0x1af): warning: `sys_nerr' is deprecated; use `strerror' or `strerror_r' instead
gcc -O2 -Wall -pipe -I..   -c -o ct.o ct.c
gcc -O2 -Wall -pipe -I..  -o ct ct.o 
make[1]: Leaving directory `/home/buc/mgetty-1.1.36/callback'
cd doc ; make "CC=gcc" "CFLAGS=-O2 -Wall -pipe -I.." "LDFLAGS=" "LIBS=" doc-all
make[1]: Entering directory `/home/buc/mgetty-1.1.36/doc'
../sedscript <mgetty.texi-in >mgetty.texi
texi2roff -ms <mgetty.texi >mgetty.ms
/bin/sh: texi2roff: not found
make[1]: [mgetty.ms] Error 127 (ignored)
nroff -ms mgetty.ms >mgetty.asc
troff: fatal error: can't find macro file s
make[1]: [mgetty.asc] Error 1 (ignored)
makeinfo mgetty.texi
make[1]: makeinfo: Command not found
make[1]: [mgetty.info] Error 127 (ignored)
texi2dvi mgetty.texi
make[1]: texi2dvi: Command not found
make[1]: [mgetty.dvi] Error 127 (ignored)
dvips -o mgetty.ps mgetty.dvi
This is dvips(k) 5.96.1 Copyright 2007 Radical Eye Software (www.radicaleye.com)
dvips: ! DVI file can't be opened.
make[1]: [mgetty.ps] Error 1 (ignored)
make `for i in g32pbm.1 g3cat.1 pbm2g3.1 sff2g3.1 fax.1 faxspool.1 faxrunq.1 faxq.1 faxrm.1 coverpg.1 mgettydefs.4 faxqueue.5 sendfax.8 mgetty.8 callback.8 faxrunqd.8 faxq-helper.8 ; do echo \`expr $i : "\([^.]*\)"\`.man ; done `
make[2]: Entering directory `/home/buc/mgetty-1.1.36/doc'
../sedscript <g32pbm.1in >g32pbm.1
nroff -man g32pbm.1 >g32pbm.man
../sedscript <g3cat.1in >g3cat.1
nroff -man g3cat.1 >g3cat.man
../sedscript <pbm2g3.1in >pbm2g3.1
nroff -man pbm2g3.1 >pbm2g3.man
../sedscript <sff2g3.1in >sff2g3.1
nroff -man sff2g3.1 >sff2g3.man
../sedscript <fax.1in >fax.1
nroff -man fax.1 >fax.man
../sedscript <faxspool.1in >faxspool.1
nroff -man faxspool.1 >faxspool.man
../sedscript <faxrunq.1in >faxrunq.1
nroff -man faxrunq.1 >faxrunq.man
../sedscript <faxq.1in >faxq.1
nroff -man faxq.1 >faxq.man
../sedscript <faxrm.1in >faxrm.1
nroff -man faxrm.1 >faxrm.man
../sedscript <coverpg.1in >coverpg.1
nroff -man coverpg.1 >coverpg.man
../sedscript <mgettydefs.4in >mgettydefs.4
nroff -man mgettydefs.4 >mgettydefs.man
../sedscript <faxqueue.5in >faxqueue.5
nroff -man faxqueue.5 >faxqueue.man
../sedscript <sendfax.8in >sendfax.8
nroff -man sendfax.8 >sendfax.man
../sedscript <mgetty.8in >mgetty.8
nroff -man mgetty.8 >mgetty.man
../sedscript <callback.8in >callback.8
nroff -man callback.8 >callback.man
../sedscript <faxrunqd.8in >faxrunqd.8
nroff -man faxrunqd.8 >faxrunqd.man
../sedscript <faxq-helper.8in >faxq-helper.8
nroff -man faxq-helper.8 >faxq-helper.man
make[2]: Leaving directory `/home/buc/mgetty-1.1.36/doc'
make[1]: Leaving directory `/home/buc/mgetty-1.1.36/doc'

```

Am I to assume my mgetty fax is installed and ready to rock?

Where is it? How do I start it?

---

### Post by talsemgeest on 2008-02-08
If it was it would move you to another command prompt...

---

### Post by rustyDusty on 2008-02-08
> **talsemgeest said:**
> If it was it would move you to another command prompt...

Is that supposed to: (pick an option)
help me :)
encourage me :popcorn:
confuse me :confused:

Please clairify because I don't know where to go from here. What can I do to get it to move me to another command prompt.

Anyway I'm about to give up on mgetty. I'm trying to use tkvoice1.5 but I have problems with that one to even though I got the interface to come up.

Go to this thread [http://ubuntuforums.org/showthread.php?t=690682](http://ubuntuforums.org/showthread.php?t=690682)  and see if you can enlighten me.

---

### Post by seventhc on 2008-02-08
shouldnt you run ./configure first?
```

./configure
make
sudo make install

```
maybe this is easier
```

sudo apt-get install mgetty

```

---

### Post by rustyDusty on 2008-02-08
Thank you for you post seventhc.

I did that and was told that mgetty is already installed.
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
mgetty is already the newest version.
The following packages were automatically installed and are no longer required:
  vim-gui-common vim-runtime
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I'm trying to set up a virtual office and I need a answering machine.

I was just told in another forum that: > 
Most answering machine programs rely on a modem (no duh!), but other than external modems, most internals, over the last 10 or more years have had little or no Linux support, because they are 'softmodems', relying mostly on Windows and the CPU to provide the modem's functionality.

Because of this most Linux coders have ignored modem based applications.

So I don't know if I'll ever get what I need from Linux virtual office wise. I might have to go back to windows :(

I'm not familiar with VOIP/Asterix/PBX software because I  just deal with local yokels who always call me when I'm out ad I don't have and don't want a stand alone answering machine because in Windows I always relied on my voice fax software/modem.

I didn't know this was going to be a major hurdle.

---

### Post by seventhc on 2008-02-08
Sorry, I can't be of much help having never used mgetty. :(

---

### Post by talsemgeest on 2008-02-08
Sorry, I was in a bit of a rush last night, so I'm sorry for making such an unclear post. I meant that because it didnt come up with another command prompt, the installer wasnt finished.
But as for your problem now, I will see what I can dig up.

---

### Post by talsemgeest on 2008-02-08
Try going into synaptic package manager, search for mgetty, and then select completely remove. Then click apply, search for mgetty again and install it.

Hope this helps :)

---

