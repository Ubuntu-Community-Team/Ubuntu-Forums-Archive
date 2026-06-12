---
title: "How Can I Format My Second Harddrive."
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by hempa on 2007-02-19
Hello! i have two harddrives with ubuntu on both. i want to format one of them how can i do this.?  and how can i see witch harddrive that im using right now with this ubuntu installation
.

---

### Post by jvc26 on 2007-02-19
I'd do:
```

sudo fdisk -l

```
That will tell you what partitions are on what disk .
Il

---

### Post by hempa on 2007-02-19
> **Illuvator said:**
> I'd do:
```

sudo fdisk -l

```
That will tell you what partitions are on what disk .
Il

thanks. wrote the fdisk command you gave me and it showed me both my harddrives. but how do i go on from here if i want to format and partition one of them??

---

### Post by vigleik on 2007-02-19
Either boot from the live CD and run the partitioning tool there, or install qtparted or gparted (or another tool) and run locally.

---

### Post by MystaMax on 2007-02-19
I like to use gParted for drive partitioning. Its easy and quick.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

you can type "man fdisk" at the commandline to find out more on using fdisk.

---

### Post by esaym on 2007-02-19
I am not sure about ubuntu but in kubuntu there is a way that you can view unmounted and unformatted disks.  You could try to install qtparted.  It can format but I don't know if it will see an unmounted disk..

sudo aptitude install qtparted

---

### Post by hempa on 2007-02-19
I have now installed GParted but how do i run it?? from th terminal or is it in a dir. somwhere

---

### Post by tagginannie on 2007-02-19
> **hempa said:**
> Hello! i have two harddrives with ubuntu on both. i want to format one of them how can i do this.?  and how can i see witch harddrive that im using right now with this ubuntu installation
.


In Linux the drives are listed differently than WIndows/DOS. In DOS you have Drive
"C" first hard drive and a second hard drive is "D". In Linux they are listed as;
DOS drive "C"    Linux hda/sda
DOS Drive "D"   Linux hdb/sdb

 (sda is for SCSI drives)

The easy way to format drives is using QTparted witch you can download using 
"Add/Remove Programs" click on System.

Suzy:KS

---

### Post by Resurrection on 2007-02-19
Just run it from a terminal, just a:

```
sudo gparted
```

---

### Post by MystaMax on 2007-02-19
> **Resurrection said:**
> Just run it from a terminal, just a:

```
sudo gparted
```



shouldn't that be:

```

gksudo gparted

```

Which desktop environment are you running? Gnome or KDE? Some are recommending the KDE way which can be confusing if you are running gnome.

If you are running gnome, go to the System Panel --> Administration --> GNOME Partition Editor

---

### Post by n8bounds on 2007-02-19
Another good (terminal) command is ```
 df -HT 
``` that shows you all the partitions YOU HAVE MOUNTED and you can compare that against the results from ```
 sudo fdisk -l 
``` which shows you ALL THE PARTITIONS MOUNTED OR NOT so when you run ```
 gksudo gparted 
``` you won't be so confused about which partition to blow away.

Don't worry too much tho.  gparted won't let you fool with partitions that you have mounted, which would be important partitions like your root and swap partition.  See if you just run the Gnome Partition Editor (gparted) from the live cd, it will be LESS obvious which partitions you are normally using and which are on your "other" hard drive.

CAIO

---

### Post by SouthernGorilla on 2007-02-22
I have successfully added a second drive to my system using GParted and the tips in this thread as well as a couple others, now I have a related question. How do I save files to it? Do I need to create a directory of some sort? Nautilus doesn't show the new drive. My system is 100% ubuntu and the extra drive just has a single ext3 partition, I just went with the GParted default settings. I'm sure I screwed something up, but the nice thing about a blank drive is that you can't ruin any data.

---

### Post by MystaMax on 2007-02-22
Try n8bounds tips. First type ```
df -HT
``` and ```
sudo fdisk -l
```and see if you get something other than /dev/hda1. Maybe /dev/hdb1 or something along those lines. If not, it means it probably didn't mount automatically when booting the system.

---

### Post by SouthernGorilla on 2007-02-22
fdisk shows the second drive, but the other command only lists the primary. It's not a master/slave setup, each drive has it's own connection to the board if that makes any difference. At least I know the system recognizes the other drive, just need to figure out how to send files to it.

---

### Post by masteryurez on 2007-02-27
You can install Gparted (Partition Manager for Gnome). Just run
> sudo apt-get install gparted
to install gparted.
After that go to System > Administration > Partition Manager for Gnome
Start the program and select the harddrive you want to format.

Have a nice day :)

---

### Post by masteryurez on 2007-02-27
You can install Gparted (Partition Manager for Gnome). Just run
```
sudo apt-get install gparted
```
to install gparted.
After that go to System > Administration > Partition Manager for Gnome
Start the program and select the harddrive you want to format.

Have a nice day :)

---

