---
title: "Brasero Multisession Gnome"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by interjaz on 2007-08-17
Hi

I downloaded the Brasero 0.5.9 from deb package.
-> [http://download.ubuntu.pl/_Feisty_Fawn/brasero/](http://download.ubuntu.pl/_Feisty_Fawn/brasero/)
I tried CD-R with multisession and this CD-R disk is acutally in trash :(.

So I thought testing with CDRW might be a better solution.

I've opened the Brasero and burned a CD-RW disk with some data. Success: 100%.
After this I tryed to open DATA and I could.

Next test was by burn on same CDRW some extra data (multisession). Success 100%.
After this i get an alert:

~$ sudo mount -v /dev/hdd /media/LiteOn
```
mount: you didn't specify a filesystem type for /dev/hdd
       I will try type iso9660
mount: Not a directory
```

I tryed to look for an answer on this forum but without a result. 

I paste some Data maybe it will help you to understand the problem:

~$ dmesg | grep RW
```
[   27.652505] hdd: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
[   27.884366] hdd: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
```

~$ cat /proc/sys/dev/cdrom/info
```
CD-ROM information, Id: cdrom.c 3.20 2003/12/17

drive name:             hdd     hdc
drive speed:            48      48
drive # of slots:       1       1
Can close tray:         1       1
Can open tray:          1       1
Can lock tray:          1       1
Can change speed:       1       1
Can select disk:        0       0
Can read multisession:  1       1
Can read MCN:           1       1
Reports media changed:  1       1
Can play audio:         1       1
Can write CD-R:         1       0
Can write CD-RW:        1       0
Can read DVD:           1       1
Can write DVD-R:        1       0
Can write DVD-RAM:      1       0
Can read MRW:           0       0
Can write MRW:          0       0
Can write RAM:          1       0
```

I thought maybe its gnome fault not multisession writing so I've tested burned CDRW on windows XP - It was clean !! but the size was smaller (data burned)

In NERO I cleaned the CDRW and made another multisession cd - works on XP
And works on UBUNTU. :lolflag:

What is the problem? I really don't get it.

---

### Post by interjaz on 2007-08-17
If you have same problems. Install K3B it works fine.

---

