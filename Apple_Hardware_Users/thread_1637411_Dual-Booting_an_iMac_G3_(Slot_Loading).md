---
title: "Dual-Booting an iMac G3 (Slot Loading)"
date: 2010-12-04
forum: Apple Hardware Users
---

### Post by donaldmartin on 2010-12-04
Hi, I purchased an iMac G3 back in January with the intent to upgrade it. That time has finally come, with me now ordering more RAM, bigger HDD, and a DVD-ROM drive. It currently runs a strange distro of Linux that I put together from scratch, however, I wish to remove that and install Mac OS 10.2 "Jaguar" and an Ubuntu distro.

Would the iMac allow this? Thanks in advance.

System Specs (currently):
PPC 350MHz Processor
192MB RAM
7GB Hard Drive
CD-ROM Drive

System Specs (planned):
PPC 350MHz Processor
1GB RAM
120GB Hard Drive
DVD-ROM Drive

---

### Post by conal on 2010-12-05
Nice upgrade plan! I have installed Linux and OS X. The easiest way to do this is to install OS X first then resize the OS X partition using gparted from an Ubuntu (or other distro) live cd.
You might know some of this stuff already:

The live/desktop CDs won't boot an all G3's so test that before you install OS X (they did on my slot loading 400Mhz, but not on my tray loading 233Mhz). I have not been able to resize OS X from an alternate ISO with any Linux distro)

I think the live CD's will work on yours, but if not you will need to partition the hard drive before installing OS X, which is a bit more complicated, you'll need to ask someone else. 

By the way Tiger runs fine on these macs, though with the really old ones you need to install 10.2 or 10.3 first then upgrade to 10.4 using Xpostfacto. If you then disable spotlight, dashboard etc it seems to run as fast as 10.3. 

Anyway. once you have resized the OS X partition I would suggest you use Debian or MintPPC rather than Ubuntu as Ubuntu on PowerPC currently has a few major bugs. Mint is Debian with modifications (like codes included),see here: [http://www.mintppc.org/content/installation-instructions](http://www.mintppc.org/content/installation-instructions)

As you probably know you really need to use a lightweight window manger on these old macs, so LXDE works well, this is what MintPPC uses by default. 

However if you are really keen to use Ubuntu there is plenty of advice on these forums on the know bugs, e.g CD's/DVD's don't automount. There is also a FAQ here: [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

This FAQ is dated, for example the mediubuntu repositories no longer work, If you need video/audio codecs etc I have posted one solution here: [http://ubuntuforums.org/showthread.php?t=1385579](http://ubuntuforums.org/showthread.php?t=1385579) though I'm sure there are more. You may struggle to play DVD's on the linux partition, I have had the most success with Ogle. 

I'd suggest you search these forums for posts by Linuxopjemac and Oswald Kelso, they both have good advice on G3's! 

Best

conal

---

### Post by conal on 2010-12-05
Oh, and where in Glasgow do you stay?

---

