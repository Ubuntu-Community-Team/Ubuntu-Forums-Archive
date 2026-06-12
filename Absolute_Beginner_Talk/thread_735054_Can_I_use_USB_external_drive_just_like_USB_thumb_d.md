---
title: "Can I use USB external drive just like USB thumb drive?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by paker on 2008-03-25
I have been using a 1 Gig USB thumb drive to transfer files from ubuntu desktop to Windows Vista laptop.  I need something larger than 1 Gig. Can I use a USB-interfaced external hard disk just like a USB thumb drive? Can I mount and unmount the external drive with the host computer on?

Related question: both computers are connected to a router. Is there a way to transfer files directly through the router? If it is not too complicated, please teach me how to.

---

### Post by LowSky on 2008-03-25
yes you can use a USB hard Drive like a thumb drive

and yes you can move files over your network it just takes some work. Is the other computer Windows or Linux based?

---

### Post by kpkeerthi on 2008-03-25
Yes you can. The external USB HDD will be automatically mounted just like a thumb drive.

---

### Post by paker on 2008-03-25
Thank you for the replies for the first question. When I get a brand new external hard disk with USB interface, should I format it first? It will be plugged to Ubuntu desktop and Windows Vista laptop.

The second question: file transfer between computers through router. One has Ubuntu 7.10 (32 bit) currently. Will upgrade to 8.04 when released. The other has Windows Vista 32 bit. I will be moving files from Ubuntu desktop to Windows laptop. 
What work needs to be done? I am pretty much network ignorant but I can google. Please give me a brief overview of what needs to be done. Thanks.

---

### Post by kpkeerthi on 2008-03-26
> **paker said:**
> Thank you for the replies for the first question. When I get a brand new external hard disk with USB interface, should I format it first? It will be plugged to Ubuntu desktop and Windows Vista laptop.
Most come preformatted as FAT32. If it is not formatted already you can format it using gparted available in Ubuntu live CD
1. Boot with Ubuntu live CD and plugin your external drive
2. Open a terminal and type **gparted** or go to System -> Admin -> Disks & Partitions
3. Right click your drive (should display as **unallocated**) and unmount it if it gets mounted automatically
4. Select 'New' from right-click menu and choose the partition type you want (FAT32/NTFS/EXT3)
5. Click Apply

See [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) for more info

> **paker said:**
> 
The second question: file transfer between computers through router. One has Ubuntu 7.10 (32 bit) currently. Will upgrade to 8.04 when released. The other has Windows Vista 32 bit. I will be moving files from Ubuntu desktop to Windows laptop. 
What work needs to be done? I am pretty much network ignorant but I can google. Please give me a brief overview of what needs to be done. Thanks.
See
[http://screencasts.ubuntu.com/SAMBA_Filesharing](http://screencasts.ubuntu.com/SAMBA_Filesharing)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

