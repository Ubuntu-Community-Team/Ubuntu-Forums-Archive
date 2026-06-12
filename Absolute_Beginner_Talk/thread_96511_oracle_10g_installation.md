---
title: "oracle 10g installation"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by ziociccio on 2005-11-29
Hi,

Does someone know what kind of pachage are necessay to install oracle 10g in ubuntu?

Is there an official guide to do that installation?

thanks a lot

Francesco

---

### Post by amohanty on 2005-11-29
[http://www.csee.wvu.edu/~ccole/oracle10g-ubuntu](http://www.csee.wvu.edu/~ccole/oracle10g-ubuntu)

Just remember to load up your boxen on RAM. 10g is a monster.

AM

---

### Post by ziociccio on 2005-11-29
I tried it but it doesn't work.

---

### Post by amohanty on 2005-11-29
Hmm, worked for me on Hoary...
so what problem did you run into?

AM

The wiki has pretty much the same thing:
[https://wiki.ubuntu.com/Oracle10g](https://wiki.ubuntu.com/Oracle10g)

Also this thread might be helpful:
[http://www.ubuntuforums.org/showthread.php?t=85513](http://www.ubuntuforums.org/showthread.php?t=85513)

---

### Post by ziociccio on 2005-11-29
The installation stops at 63% because it didn't find libagtsh.so
this is the part of the error log:

/home/oracle/oracle/product/10.2.0/db_2/lib//libagtsh.so: undefined reference to `nnfyboot'

are this package inside ubuntu or I have to download from debian site?
gcc, make, binutils, lesstif2, libc6

---

### Post by amohanty on 2005-11-29
> are this package inside ubuntu or I have to download from debian site?
gcc, make, binutils, lesstif2, libc6

use synaptic 
System->Administration->Synaptic Package Manager
to install these. 

You can also use apt-get
In a terminal
Applications->Accesories->Terminal 
type:
sudo apt-get install gcc make binutils lesstif2 libc6 libc6-dev rpm

For that problem see this post: http://groups.google.com/group/comp.databases.oracle.misc/browse_thread/thread/2e08e3d61a361c8b/ee87ffcb3590a598?lnk=st&q=libagtsh.so%3A+undefined+reference+to+%60nnfyboot'&rnum=2#ee87ffcb3590a598

HTH
AM

---

### Post by ziociccio on 2005-11-29
I've read this post but there are specified a lot of  package:
binutils 
libdb2 
libdb3 
libdb4.1 
libdb1-compat 
cpp-3.3 
gcc-3.3 
libstdc++5-3.3-dev 
libstdc++2.10-glibc2.2 
base-files 
netbase 
libc6 
libc6-dev 
make 

are they in ubuntu?
libdb4.1 exists only for 64 bit environment, in debian site...

---

### Post by amohanty on 2005-11-29
I think most of them do

for make do this:
sudo apt-get install build-essentials 

I think you can ignore the debian site for now, and search in synaptic. If there is something here that you dont find via synaptic please post it here.

AM

---

### Post by ziociccio on 2005-11-29
OK,

thanks a lot.

Francesco

---

### Post by daacon on 2005-11-29
Just went through this on the weekend

[http://ubuntuforums.org/showthread.php?t=16654&page=2&highlight=oracle+10g](http://ubuntuforums.org/showthread.php?t=16654&page=2&highlight=oracle+10g)


That worked for me - albiet after a couple attemtps :-) and yep if you use db assistant to create a db Oracle 10g demands a minimum of 43% of your RAM (for me anyway I have 512 ram) - for me this is about all Iwanted to run (Oracle ) so not a big concern. 

later............dy

---

### Post by ziociccio on 2005-11-30
The problem already persists.

I tried to install gcc, make, binutils, lesstif2, libc6, rmp but these libreries need other library that I downloaded from Debian site.

At the end: I need to configure gcc 3.3... and this library needs libstdc++5-3.3.

If I try to install libstdc++5-3.3, it tells me it requires gcc 3.3.... a kind of loop!!!!

Here the log:
francesco@acerubuntu:~/Desktop$ sudo dpkg -i libstdc++5-3.3-dev_3.3.6-7_i386.deb
(Lettura del database ... 78127 file e directory attualmente installati.)
Mi preparo a sostituire libstdc++5-3.3-dev 1:3.3.6-7 (con libstdc++5-3.3-dev_3.3.6-7_i386.deb) ...
Spacchetto il rimpiazzo di libstdc++5-3.3-dev ...
dpkg: problemi con le dipendenze impediscono la configurazione di libstdc++5-3.3-dev:
 libstdc++5-3.3-dev dipende da g++-3.3 (>= 1:3.3.6-7); comunque:
  Il pacchetto g++-3.3 non è ancora configurato.
dpkg: errore processando libstdc++5-3.3-dev (--install):
 problemi con le dipendenze - lasciato non configurato
Sono occorsi degli errori processando:
 libstdc++5-3.3-dev
francesco@acerubuntu:~/Desktop$ sudo dpkg -i g++-3.3_3.3.6-10_i386.deb
(Lettura del database ... 78127 file e directory attualmente installati.)
Mi preparo a sostituire g++-3.3 1:3.3.6-10 (con g++-3.3_3.3.6-10_i386.deb) ...
Spacchetto il rimpiazzo di g++-3.3 ...
dpkg: problemi con le dipendenze impediscono la configurazione di g++-3.3:
 g++-3.3 dipende da libstdc++5-3.3-dev (= 1:3.3.6-10); comunque:
  La versione di libstdc++5-3.3-dev nel sistema è 1:3.3.6-7.
dpkg: errore processando g++-3.3 (--install):
 problemi con le dipendenze - lasciato non configurato
Sono occorsi degli errori processando:
 g++-3.3


Any suggestion?

---

### Post by daacon on 2005-11-30
Did you use Snaptic Package Manager ? It will pick up the dependencies - that worked for me for all the packages expect I had to choose lib6c-dev manually (C header files)  and I downloaded lesstif2 from some web site. 

All other pacakges recommended in the Doc I used were listed in the Synaptic Package Manager (I am a Ubuntu newbie as well so not sure how the sudo apt-get command works I have had no need to use it yet)

---

