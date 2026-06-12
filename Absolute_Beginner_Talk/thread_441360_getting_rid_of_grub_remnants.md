---
title: "getting rid of grub remnants"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by river16 on 2007-05-12
Hello all!

 I was an idiot and I did not look for how to uninstall Ubuntu beforehand, so I went ahead and deleted its partition. Well later when I tried to reboot, I kept getting a grub 22 error. I now know that Grub has left some files on my xp mbr. 

So I downloaded a little workaround that boots an mbr from a cd, and I was able to boot into windows! Anyway is there anyway for me to fix my mbr without the windows xp install cds or is there anywhere I can download them for free? If so please let me know thanks!

BTW I still have ubuntu on my laptop, VIVA LINUX!

---

### Post by alienexplorers on 2007-05-12
Install you windows cd into recovery mode.  Enter fixmbr & fixboot.

---

### Post by river16 on 2007-05-12
i would love to but i dont have a windows recovery cd, my pc came preconfigured with it.

---

### Post by starcraft.man on 2007-05-12
> **river16 said:**
> i would love to but i dont have a windows recovery cd, my pc came preconfigured with it.

You must either have gotten recovery CDs or have a hidden partition on the drive with your set up files (I have that)  to access the partition if you don't have CDs you usually interrupt the start up of the computer at the manufacturer screen (push enter/esc) and then select to recover your system. 

If you don't have that option from your manufacturer on a hidden partition, then your hosed and you must have deleted it when you installed Ubuntu. Then, your only alternative is to buy new windows cd or go on a torrent site to get a new copy, should be able to use your old key with it.

---

### Post by jiminycricket on 2007-05-12
There's apprently an exe file that can be run in Windows to do that, I've tried it myself and it didn't have a virus but check it out as always with any windows exe: [http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

---

### Post by gn2 on 2007-05-12
This should help: [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

