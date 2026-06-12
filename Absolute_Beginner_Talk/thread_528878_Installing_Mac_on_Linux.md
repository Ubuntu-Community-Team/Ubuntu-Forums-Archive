---
title: "Installing Mac on Linux"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by WarholsGhost on 2007-08-18
I am trying to install mac on linux. i obtained the tar.bz2 file and extracted it, then in the terminal i tried to run ./configure and i get this message. 

gregg@gregg-desktop:~/Desktop/mol-0.9.72.1$ ./configure
./autogen.sh
==================================================
 Invoking autoheader and autoconf.
./autogen.sh: 20: autoheader: not found
autoheader failed


how can i get this working?

---

### Post by Tomosaur on 2007-08-18
Do you mean 'Mac' as in the operating system? Do you have a link to where you got this file from?

---

### Post by kellemes on 2007-08-18
Sure.. OSX in a tarball

---

### Post by wirelessmonkey on 2007-08-18
Instead of ./configure, type autoconf and if it fails post the output. You may have to install autoheader... i.e. sudo apt-get autoheader, or the package that contains autoheader, which I cant recall off the top of my head, but I think is w/ autoconf.

---

### Post by fearevilleet on 2007-08-18
I still dont get what OSX in a tarball is?  Did you just take an osx cd and put it in a tar file? Do you have a link so we could get more info?

---

### Post by WebSiteGuru on 2007-08-18
> **fearevilleet said:**
> I still dont get what OSX in a tarball is?  Did you just take an osx cd and put it in a tar file? Do you have a link so we could get more info?

That's what I would like to know too.

---

### Post by testube_babies on 2007-08-18
[http://mac-on-linux.sourceforge.net/news.php](http://mac-on-linux.sourceforge.net/news.php)

I think it's PowerPC only...

Also, you should use ./autogen.sh and not ./configure

---

### Post by fearevilleet on 2007-08-18
from their wiki
"Mac-On-Linux provides a virtual machine for running MacOS, MacOSX and Linux (in progress) on your PowerPC machine."

So unless you have a ppc cpu it wont work

---

### Post by spikestudios on 2008-04-07
Try
> sudo apt-get install autoconf


---

### Post by SOULRiDER on 2008-04-07
Is it similar to sheepshaver? I wrote a tutorial on how to install sheepshaver from source:
[http://ubuntuforums.org/showthread.php?t=670336](http://ubuntuforums.org/showthread.php?t=670336)

---

