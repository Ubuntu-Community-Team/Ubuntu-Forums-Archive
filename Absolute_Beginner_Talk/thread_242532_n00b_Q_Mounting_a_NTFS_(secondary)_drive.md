---
title: "n00b Q: Mounting a NTFS (secondary) drive"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by anthonyp on 2006-08-23
Ok firstly id like to say I have never used ubuntu (linux) b4 in my life. Closest i have been to the terminal style of computing is DOS about 14 years ago.

Here is my scenario... Installed Ubuntu on a fresh 160gb SATA hdd yesterday arvo (ext3 format).
I have a secondary HDD that is the same brand 160gb SATA but its in NTFS format (from and old XP machine).
This secondary drive contains afew rips off my cds and alot of pictures and the mydocuments folder from and old windows that i want to retrieve.

I want to copy the stuff to the Linux (ext3) main drive, then format the secondary (ntfs) drive to the new ext3 format.
Then i wish to copy the info back to the secondary hard drive.

BUT (and its a big but), I have no idea how to get the info from the secondary hdd to the main (ext3) linux drive.

I have searched and read abit (even tried one suggestion) with no sucess.

Wat i need is a basic, total laymens terms description, on the best way to do this... the terminal is scary but i am def willing to learn as i truely am sick of windows XP.

The main use for my PC is general browsing, messenging, excel spreadsheets, and music and photo storage/viewing.

My PC Specs:
AMD Athlon 64 3500+
Ubuntu 6.06 OS (64bit)
1gb DDR400
Dual 160gb SATA HDD (primary ext3, secondary NTFS)
NVidia GeForce PCI-E Graphics on ASUS Nforce board (not sure of the name)


Cheers
Anthony 

p.s. thanks in advance to all that can help me.:redface:

---

### Post by bodhi.zazen on 2006-08-23
General steps:

This is all done in a terminal. You will get used to it.

1. Make mount point.

2. Mount windows partition.

3. Copy files & fromatting I will leave aside for now (ask if you need help).

In a terminal enter the following set of commands:
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sdb1 /media/windows
```

You can copy your files from /media/windows now, then format.

---

### Post by anthonyp on 2006-08-24
Thank you I can see where i went wrong in my last attempt.

Ill try this as soon as i get home.... then i think i have copying and def have formatting down pat.

Cheers
Anthony

---

### Post by anthonyp on 2006-08-24
special device /dev/sbd1 does not exist  :(

---

### Post by bodhi.zazen on 2006-08-24
Sorry. What partition is you windows drive?

Try hdb1, sda1, hdb2, sda2, hda, hdb. One of these should work.

---

### Post by anthonyp on 2006-08-24
I got it working by using the apt-get diskmounter (found it through links on the forum) and it pretty much automatically downloaded and setup to mount the drive on boot. :D 

The link is int he first post of this thread for anyone whom is in my same position.
[http://www.ubuntuforums.org/showthread.php?t=242584&highlight=diskmounter](http://www.ubuntuforums.org/showthread.php?t=242584&highlight=diskmounter)


All my info that i need is now coppied to /home/grimace and i am just waiting abit to format it to make sure everything is workin well.

Thansk for the help guys... now to find out how to play my mp3s ](*,)  a new thread :) 

Cheers
Grimace

---

### Post by bodhi.zazen on 2006-08-24
Try this:
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Search the page for mp3 or xmms.

---

