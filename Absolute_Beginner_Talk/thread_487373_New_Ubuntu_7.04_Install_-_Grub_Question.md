---
title: "New Ubuntu 7.04 Install - Grub Question"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by chrisf79 on 2007-06-29
Greetings:

I have one Serial ATA hard drive in my machine and SDA1 is the partition windows is on.  I made three new partitions for Ubuntu (one for /, one for /boot and a swap partition).  When I've clicked through the install process, I have the page that shows what the install is about to do.  There's the "Advanced Options" button that says Grub will be installed on (hd0).  What should I change that to if I want grub installed on this one Serial ATA hard drive I have?  I tried changing it to (sda) but once install had finished copying the files, it told me that it encountered a fatal error installing Grub.  I'm a little lost on this one so any help would be greatly appreciated!

---

### Post by coldstatue on 2007-06-29
hd0 is the first drive the install sees. sda and hd0 are one and the same. sda is the device id linux identifies the drive with, and you will have patitions listed as sda1, sda2, etc. You will see the hd ids as hd0,1 hd0,2 etc. I think the hd partition ids start at 0, but I'm not sure. hd0,0, hd0,1, etc.

Do you have any other drives on the system?

---

### Post by coldstatue on 2007-06-29
BTW - when it asks if you want to install on to the MBR, say yes. I tried all kinds of alternatives out of fear for messing up my Windows install, and it is, bar far, the most reliable and simple method. Don't bother with Windows-based bootloaders. They're nothing but trouble.

---

