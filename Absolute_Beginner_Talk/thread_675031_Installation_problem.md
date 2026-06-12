---
title: "Installation problem"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by etomic13 on 2008-01-22
so I formatted the disc on my new compaq f500 and was ready to load up ubuntu and as soon as it started to install it ran into an error 
The creation of swap space in partition #5 of SCSI1 (0,0,0) (sda) failed

its definitely not a scsi drive either, this makes no sense.

---

### Post by djbsteart1 on 2008-01-22
did you just select the option where ubunut installs automatically, or did you partition the disk yourself?
if it was automatic try to set up swap yourself in the partition manager, or if you tried to do it manually, check everything over and try again, or if you want to use the whole disk, try the automatic setting. what version are you using?

---

### Post by etomic13 on 2008-01-22
First I used the automatic guided setting and it produced a similar error about it being unable to create an ext3 partition. I have Gparted open and Im changing my NTFS partition to ext3 and trying again. Even Gparted couldnt create the partition it gave an error about creating ext3.

---

### Post by djbsteart1 on 2008-01-23
right, try qparted but i would get hopeful, it seems to be slightly out of my depth now, if neither of the settings work. you could have a trawl through the repositories to find different programs for partitioning. also if gparted loads, try a different file system, and make sure the system is up to date before starting. in terminal type:
```
sudo apt-get update
```

```
sudo apt-get install
```

then try again. if this doesnt work them im out, sorry i couldnt help more.

---

### Post by rosegarden78 on 2008-01-23
Is this your first time using partitions.  It can be scary I know.  Just always use Primary partitions.  Never use Extended partitions.  Don't ask why!  You'll be sorry later.

---

### Post by housam on 2008-01-23
Try to use the newer version of Gparted. download and burn the live CD from [COLOR="Red"][[COLOR="Red"]this site[/COLOR]]("http://gparted-livecd.tuxfamily.org/")[/COLOR]

---

