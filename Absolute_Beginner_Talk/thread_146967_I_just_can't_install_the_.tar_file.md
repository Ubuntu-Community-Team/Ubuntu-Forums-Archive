---
title: "I just can't install the .tar file"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by RRanciDD on 2006-03-19
:-k After installing ubuntu i'd try to install some "drivers" of rt2500 of a pcmcia wireless, but the permissions won't allow me.

I'd try thru the terminal, /media/mypendrive, and it said it didn't exist or something... in the "desktop user friendly" I can reach the usbpendrive and unpack the drivers but not to the filesystem, cause it says i don't have permission.:evil: 

Please help me, I'm really trying to move out of windows but without internet it's hard to do that:cry: 

Please\\:D/

---

### Post by jjf on 2006-03-19
Hi, Rancid.  It would help if you could be a little more clear about what you're trying to do.  You have the drivers for your PCMCIA Wireless Card on a USB flash drive, but you get an error about permissions when you try to access certain files on the flash drive?

A .tar file is an archived file.  If you double-click it, it will bring up the un-archiving program.  You need to click the extract button to extract ("unzip") those files to your desktop.  You can't really do anything with the files archived inside a tar until you extract them.  That may be what your error message means.

---

### Post by jakez on 2006-03-19
Maybe this will help:
[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo)
greetz

---

### Post by steve.horsley on 2006-03-19
For info about permissions, read [https://wiki.ubuntu.com/RootSudo/](https://wiki.ubuntu.com/RootSudo/)

So from the command line, un-tar it with **sudo tar xvf whatever.tar** or use  nautilus with root privilege by launchng it like this: **gksudo nautilus**, but be careful - you can wipe the whole disk with one mistake when runing Nautilus at root.

---

### Post by RRanciDD on 2006-03-19
Ok... i'll try it.

Thanx\\:D/

---

### Post by RRanciDD on 2006-03-19
It work out great!

Thanx... I m writting this with linux running.

---

