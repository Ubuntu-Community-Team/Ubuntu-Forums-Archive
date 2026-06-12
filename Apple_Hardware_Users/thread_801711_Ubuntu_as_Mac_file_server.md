---
title: "Ubuntu as Mac file server?"
date: 2008-05-20
forum: Apple Hardware Users
---

### Post by sit-ubu-sit on 2008-05-20
I am a Mac user.  Although I've investigated, and have a few times installed, Linux distributions (other than Ubuntu), I am basically new to Linux.  I have purchased a CoolerMaster chassis, with power supply and Ethernet card.  I have not yet purchased a motherboard.  My goal is to purchase a motherboard, install a hard drive, put Ubuntu on the system, and use the box as a file server on a home network.  The trick is that I want to install additonal internal hard drives that are currently formatted as HFS+ Journaled, and have those files accessible by the Macs on my network (all running Leopard).

Is this possible, and if so, can anyone suggest a motherboard, and does anyone have any pointers on how I can set this up?

Thanks for any help!

---

### Post by cyberdork33 on 2008-05-20
I would suggest moving files off the HFS+ file systems and onto something Linux native. You can create shares with [netatalk]("http://netatalk.sourceforge.net/") for AFP or you can do NFS or even Samba

---

### Post by Thirtysixway on 2008-05-20
I would suggest samba, it's not too hard to setup.

---

### Post by sit-ubu-sit on 2008-05-21
Thank you both for your replies.  What file system would you suggest?  I would prefer something journaled that the macs can write to natively (if possible).  Also, what are the pros and cons of setting up samba versus using netatalk?

---

### Post by cyberdork33 on 2008-05-21
> **sit-ubu-sit said:**
> Thank you both for your replies.  What file system would you suggest?  I would prefer something journaled that the macs can write to natively (if possible).  Also, what are the pros and cons of setting up samba versus using netatalk?
You don't need a Mac-native filesystem to create a network share. If you are going to have the data on a Linux box, then it is best to have something that linux will be able to use reliably. HFS+ is not reliable in Linux.


Your choices for cross-compatible filesystems are HFS+ (poor in linux), ext3 (not so great in OSX anymore), ntfs (using MacFUSE in OSX), and FAT32 (nonjournaled, filesize limitations). By far, the most compatible filesystem is FAT32, but I wouldn't use that for your intended application. ext3 is very, very reliable, I would just use that.

Well, Samba is a windows sharing system and you are not using windows (and the samba issues with Leopard abound, just google it).
NFS is a Unix-native sharing system well-supported by OSX (and linux). 
netatalk is an implementation of appletalk. It is AFP 3.1 compliant. [http://netatalk.sourceforge.net/wiki/index.php/WhatIsNetatalkFor](http://netatalk.sourceforge.net/wiki/index.php/WhatIsNetatalkFor)

I'd say that samba is the easiest to setup though.

---

### Post by xdracco on 2012-09-24
Use ext4 and enable journaling... also, use Netatalk/Avahi over Samba. Netatalk was created specifically for Macs while Samba was created specifically for Windows. Granted, both work regardless of client.

Netatalk is much easier to configure. Samba requires way too much fine tuning and it has well over a hundred options. Netatalk is straight forward, easy to set up.

> **cyberdork33 said:**
> I'd say that samba is the easiest to setup though.

Really? Interesting. I've been using Samba for well over 10 years. Just recently I switched to Netatalk after switching to OSX. I found netatalk much much easier to configure. Samba has hundreds of options while Netatalk has just a fraction.

---

