---
title: "slave drive partitioned?"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by firebird45331 on 2006-07-02
today I set up my 40 Gb master drive with a partition to run XP and Ubuntu.  I was in XP and noticed that my 300 GB slave is only reporting as 20 gb.  In ubuntu it's not even showing my 2nd hard drive which is cool cause more or less that's the way I wanted it, but where did my roughly 270 gb's go?

---

### Post by steve.horsley on 2006-07-02
Dunno. What does Ububtu say to the command
**sudo fdisk -l**

---

### Post by louis_nichols on 2006-07-02
perhaps the slave drive only has that much space formatted. try formatting the rest, too. you can do that in xp by right-clicking on My Computer and choosing "manage". then go to disk management and there you should see the empty space on the slave drive as unformatted. just right click on it and format is as you like ;)

---

### Post by firebird45331 on 2006-07-02
[QUOTE=louis_nichols]perhaps the slave drive only has that much space formatted. try formatting the rest, too. you can do that in xp by right-clicking on My Computer and choosing "manage". then go to disk management and there you should see the empty space on the slave drive as unformatted. just right click on it and format is as you like ;)[/QUOTE]

that's kinda exactly what happened I don't know how it happened because before the full 300 gb was formatted.  I went back and set up another partion and formatted it with my maxtor utility that came with the hard drive and it all came back.  It added a second partition but it's all there.

---

### Post by catlett on 2006-07-02
FYI
Gparted Live is a live cd that runs the application gparted. You download it here and burn the iso to disk and boot to it. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) It's a small download, only 30mb.
This application can resize partitions, if you want. You mat want the second partition but I thought I would throw it out there.

P.S. To do it select the 2nd partition and delete it. Then select the 1st partition and select resize. It will give you an option to resize it to any size,  but just select all of it to make the drive one partition.

---

