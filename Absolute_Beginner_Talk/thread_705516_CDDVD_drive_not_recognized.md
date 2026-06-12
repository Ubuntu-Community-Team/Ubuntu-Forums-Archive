---
title: "CD/DVD drive not recognized"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by ahurd on 2008-02-23
I am running Kabuntu Feisty. Putting a disk in the drive usually results in a popup (I guess automount) asking me what I want to do. Just noticed this is not happening any more. Also System Menu -->Storage Media doesn't show CD drive. Also, Deepburner (wine) burning software shows "no drives found". I am also running win2000 in dual boot and also as a virtualbox VM. In the win2000 boot the drive is recognized by software bot not it seems in the win2000 VM. I have been having problems with burning software, k3b, gnomebaker, etc. Is this the final culmination? Could someone help me find out what has happened?

---

### Post by Squish on 2008-02-25
Well, I can suggest a possible reason ~ check the hardware, and make sure the jumper is set correctly. If it shows up in the bios, then it should be configured right (assuming it is master)

---

### Post by herbster on 2008-02-25
Okay, so your drive does work booting into Win2K but immediately booting out of that, and then booting into Ubuntu it does not?

Paste output of:

```
cat /etc/fstab
```

---

### Post by adlin5000 on 2008-02-27
I think I am having the same problem. Everything will be working fine, then randomly xubuntu will "forget" that it has a cd-r drive. It wont show in /dev/, /media/, or with lshw. I've checked all cables/jumpers/power, all good. ctrl-alt-bksp and it still won't show. If I do a complete shutdown and restart, it will come back. this has happened three or four times. I haven't been able to come up with a common event when it happens because I don't realize its missing until I try to read a cd. 

any suggestions on things I should run next time this happens to try and figure this out?

Thanks.

---

### Post by herbster on 2008-02-28
Do you use nautilus as a file browser? And when this happens, can you eject your drive?

---

### Post by adlin5000 on 2008-02-28
I'm using xubuntu, it uses Thunar. I can eject it by pressing the button on the drive, but not from xubuntu. Even using eject cdrom1 from terminal doesn't work.

---

### Post by S15_88 on 2008-02-28
sometimes your cdrom drive isn't always labeled/mounted in the default spot. for example all the programs in ubuntu think my dvd+rewriteable is located dev/cdrom but it's actually /media/cdrom0

try just typing eject cdrom see if that works

Thanks, ALain

---

### Post by adlin5000 on 2008-02-29
Yep, tried that. I did cdrom, cdrom0, cdrom1, /dev/, and /media/ and every combo of them.

Now I know just enough to get myself into trouble, so If I am mistaken, someone please correct me.
/dev/ is the drive itself, and /media/ is where the cd/file system data is mounted correct?

---

### Post by herbster on 2008-03-01
Yes, /dev be the devices and /media is the mount point Ubuntu uses.

Can you paste the output of your /etc/fstab?

```
cat /etc/fstab
```

---

### Post by adlin5000 on 2008-03-02
its cdrom1 thats been giving me the problems


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=48130b45-3dd1-47bf-bffb-a5b67cd07a0a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=fc5b0faf-45a6-45fc-82c6-e2dd4e8ce4a2 /media/sdb1     ext3    defaults        0       2
# /dev/sdb2
UUID=ec37fd79-6e66-425c-89a4-6098ab0c066d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

And if it helps, here is the relevant part of a lshw

```

id:	cdrom:0
description: 	DVD reader
product: 	DVD-ROM GD-5000
vendor: 	HITACHI
physical id: 	2
bus info: 	scsi@1:0.0.0
logical name: 	/dev/cdrom
logical name: 	/dev/dvd
logical name: 	/dev/scd0
logical name: 	/dev/sr0
version: 	0213
capabilities: 	removable audio dvd
configuration:	
ansiversion	=	5
status	=	open

id:	cdrom:1
description: 	CD-R/CD-RW writer
product: 	CD-RW SOHR-5239V
vendor: 	LITE-ON
physical id: 	3
bus info: 	scsi@1:0.1.0
logical name: 	/dev/cdrom1
logical name: 	/dev/scd1
logical name: 	/dev/sr1
version: 	2$0E
capabilities: 	removable audio cd-r cd-rw
configuration:	
ansiversion	=	5
status	=	open
```

---

### Post by Shazaam on 2008-03-02
Not an answer but a tip. When you can't eject a cd/dvd open terminal and type in....
```
sudo eject
```

---

