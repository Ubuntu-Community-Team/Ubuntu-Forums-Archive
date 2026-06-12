---
title: "PartImage - Basic help reqd"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by SnakeHips on 2007-06-17
I've installed partimage from Synaptic package manager and can logon thru terminal as SU.

pete@myplace:~$ sudo -s -H
Password:
root@myplace:/home/pete# 

I then type 'partimage' and it loads ,this is where I need a little help.

1. it says I have to umount /dev/sda1 but i'm not allowed because it's in use ??

What do I do ?

---

### Post by steve.horsley on 2007-06-17
I have always run partimage from a live CD in order to avoid this catch-22.

---

### Post by starcraft.man on 2007-06-17
I agree with steve, I also image exclusively from a live cd.
[URL="http://www.sysresccd.org/Main_Page"]
Use the system disk here,[/URL] its great and has all the tools you need, including partimage.

If you need any help getting started with it, [check aysiu's page on it.]("http://www.psychocats.net/ubuntu/partimage")

---

### Post by SnakeHips on 2007-06-17
downloaded systemrescuecd-x86-0.3.6.iso from
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
burned this to CD.
saved this page (complete) to my data partition for reference.
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
shut down and booted from livecd
opened the partimage.html i saved on data partition.
**went thru the steps and realised i needed to be connected to the net for this to work**
used this trusty peice of work to install my adsl:
usbadslmodemmanager_0.4.3.deb
.........so ,back to 
sudo aptitude update && sudo aptitude install partimage
went thru the screens and tried a couple of times but got "you dont have permissions etc"...........a little more digging pointed me to the *filename/path* so decided to save image to : /media/disk/image and hey presto ,off it went. FSCK crashed twice and i sent the report to the dev team but guessed it maybe did'nt like my SATA drive ,continued and now have 4.93Gig image compressed into TWO gzip files 2Gig and 1Gig - was most impressed the program intelligently saved it to /sda2 with 60GIg of space :-)

So ,thanks for your help guys..............now should i take a chance and try the restore process.......not today i think.

---

