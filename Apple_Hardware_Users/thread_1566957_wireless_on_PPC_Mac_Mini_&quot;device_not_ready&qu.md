---
title: "wireless on PPC Mac Mini &quot;device not ready&quot;"
date: 2010-09-03
forum: Apple Hardware Users
---

### Post by Hakimjo on 2010-09-03
I want to give a new life to my old Mac Mini that has become too weak for Mac OS ...

I successfully installed the Ubuntu 9.10 PPC version (alternate) on the machine.  EXCEPT for the support of the wifi antenna.  Network manager says: "device not ready".  I suppose there is a standard tweak to get over this hurdle.  Can anybody tell me ?

Thanks a lot !

Joachim

---

### Post by linuxopjemac on 2010-09-03
give us the output of:
```
lspci
lsusb
```
please

I want to know what kind of wireless card is installed.

---

### Post by Hakimjo on 2010-10-23
Thanks for helping.  I didn't have the machine at hand and therefore couldn't reply.
I then could hook it on a wired access, update to 10.10 and use the Gnome additional hardware driver utility.  This found and installed a driver for that wifi (airport) antenna and all works nicely.

Will post new thread for additional problems ...

---

### Post by linuxopjemac on 2010-10-24
If you find your MacMini too slow with Ubuntu 10.10, you might want to install MintPPC. It's much lighter, so faster.

---

### Post by Hakimjo on 2010-10-25
Thanks for the suggestion for Mint PPC.  I would certainly do it.  But I just finished installing 10.10 Gnome, Xfce and Kde.  I got rid again of the Kde desktop, which is definitely too slow on that small machine.  Gnome and Xfce work just fine and I can't decide yet which would be the better to use.  And elements of all three packages are actually available and useful.

What is the argument that would convince me to start all over again with Mint ;-)  Or can I just add Mint to this installation and chose to boot / log into a Mint session instead of Xfce ?

j

---

### Post by linuxopjemac on 2010-10-25
The argument is that Mint PPC is much faster, and has better support for PowerPC machines. You will find some bugs with Ubuntu, which are not present in MintPPC. Up to you.

MintPPC is Debian based, so you cannot install MintPPC on top of Ubuntu.

---

