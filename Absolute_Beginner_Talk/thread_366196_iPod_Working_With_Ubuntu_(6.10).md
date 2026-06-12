---
title: "iPod Working With Ubuntu (6.10)"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by AdrenalineJunkie on 2007-02-20
Okay basically when i plug in my 2G iPod Nano (8gb) it doesn't mount automatically ~(or work what at all)~

So basicly i would be very appreciative of **Very** detailed instructions on how to get it to work.

Many different solutions welcome.

Thanks in advance.

AdrenalineJunkie

---

### Post by justin whitaker on 2007-02-20
I fixed it very simply: there is a package in synaptic that is called usbmount. 

[http://packages.ubuntu.com/edgy/admin/usbmount](http://packages.ubuntu.com/edgy/admin/usbmount)

To which I added usbmgr. 

[http://packages.ubuntu.com/edgy/admin/usbmgr](http://packages.ubuntu.com/edgy/admin/usbmgr)

To load usb modules automatically. 

That fixed it. Just do a search for USB in synaptic. 

I use gtkpod and rhythmbox to manage my iPod mini. Just make sure that the iPod is up to date and reformatted. I find it works better that way.

---

### Post by NewOldTimer on 2007-02-20
maybe some more help
[http://doc.gwos.org/index.php/IPod](http://doc.gwos.org/index.php/IPod)

---

### Post by AdrenalineJunkie on 2007-02-20
Okay, well i have had some progress, the iPod now shows up in 'computer'

However, when i attempt to open it i get the following error;

> **Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.**

mount: wrong fs type, bad option, bad superblock on /dev/sdb,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



mount: wrong fs type, bad option, bad superblock on /dev/sdb,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



error: could not execute pmount

---

### Post by dcj65 on 2007-02-20
All I did was install Banshee and my Ipod works fine, the only thing is if you purchased songs through ITunes they won't play on Banshee

---

### Post by AdrenalineJunkie on 2007-02-21
Thank you for the help, It is now working *for now* :).

---

