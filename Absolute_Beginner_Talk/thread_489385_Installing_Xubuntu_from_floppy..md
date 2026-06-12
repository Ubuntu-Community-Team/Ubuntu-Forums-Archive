---
title: "Installing Xubuntu from floppy."
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by mastersync on 2007-07-01
I need help on installing Xubuntu. Xubuntu doesn't read my external CD-Drive after detecting cd-drive screen.

I guess I have to transfer the alt iso to partition then run loadlin or tomsrtbt to install the xubuntu. I plan to transfer the iso using cd.


Will this plan work ?

Thanks!

---

### Post by overdrank on 2007-07-01
> **mastersync said:**
> I need help on installing Xubuntu. Xubuntu doesn't read my external CD-Drive after detecting cd-drive screen.

I guess I have to transfer the alt iso to partition then run loadlin or tomsrtbt to install the xubuntu. I plan to transfer the iso using cd.


Will this plan work ?

Thanks!

Hi I just have to ask, is the system bios set to boot to cd first? Also what are the specs on the system like memory and video?
I have installed via a external cd before and have had no problems is why I am asking.

---

### Post by mastersync on 2007-07-01
Yes, it does boot the cd but it stuck after detecting cd-rom drive.

500Mhz, 128mb and 64mb video.

Thanks!

---

### Post by arochester on 2007-07-01
You need a bootdisk. It's a floppy which hands over the the CD-Rom. So you can boot from the floppy first and use the CD.. You can either use a dedicated boot disk or run something like smartbootmanager - see [http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

---

### Post by overdrank on 2007-07-01
> **mastersync said:**
> Yes, it does boot the cd but it stuck after detecting cd-rom drive.

500Mhz, 128mb and 64mb video.

Thanks!

Ok so it stuck like in frozen.  I quote from the web site
Minimum system requirements
To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only required you to have 64 MB RAM. 
I assume we are using a desktop and the video card has its on 64mb of ram. You could have a bad stick of ram also.

---

### Post by mastersync on 2007-07-01
I can only use one at a time, Floppy or CD.

---

### Post by mastersync on 2007-07-01
> **overdrank said:**
> Ok so it stuck like in frozen.  I quote from the web site
Minimum system requirements
To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only required you to have 64 MB RAM. 
I assume we are using a desktop and the video card has its on 64mb of ram. You could have a bad stick of ram also.


I'm using alternate with command line install.

EDIT : I found this : [http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html]("http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html")

---

