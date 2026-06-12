---
title: "Adding a second HDD - problems"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by jonathanapples on 2007-03-20
Hi all,

I am just new to Ubuntu and have sucessfully installed it on my old XP machine. I am using a freshly formatted 80Gb HDD.

The problem is that i would like to add my 300Gb data Hard Disk that i used to use. 

I connected it in the right way - making it a primary slave.

My problem is that upon a sudo fdisk -l command, i see the following:

It seems like there may be a problem(?) with hdb - i dont want to try mounting it unless i get some advice first!


Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/hdb2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hdb3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/hdb4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

---

### Post by ferg on 2007-03-20
Has it got data on? if not, you could just format it using gparted.
 
Let us know.

---

### Post by frodon on 2007-03-20
Sounds like hardware issue to me, check again the jumper position, the best if you are not sure is to put the jumper in the "cable select" mode. Check also the connection of your hard drive to see if something isn't badly connected.
If your hdd isn't damaged this output doesn't make sense.

---

### Post by jonathanapples on 2007-03-20
Yeh, there is a fair bit of data on there-mostly mp3's and Tv shows etc... I will check the connections etc.. and get back.

---

### Post by justleen on 2007-03-20
ive had this.. It means your partition table is f****d..

I did fix this though, ill have a search, see if i vcan find that solution again!

---

### Post by ferg on 2007-03-20
Agree with justleen - sounds like the part table has screwed intself up somehow. Never really encountered this problem and tried to recover data before. Sorry! :)

---

### Post by jonathanapples on 2007-03-20
ah bugger! I hope i can still get some of the data from it!

---

### Post by ferg on 2007-03-20
What filesystem does this disk use?

---

### Post by jonathanapples on 2007-03-20
It was NTFS when it was connected to my windows machine

---

### Post by justleen on 2007-03-20
if you have another 300gb drive.. (huhuh :) ) make an image with dd!
that way at least you have a backup..

ive found this thread so far [http://ubuntuforums.org/showthread.php?p=2210436](http://ubuntuforums.org/showthread.php?p=2210436)
not my original solution.. il keep you posted on that!

---

### Post by frodon on 2007-03-20
To recover your datas you can use "ddrescue" or "[testdisk]("http://ubuntuforums.org/showthread.php?t=387922")"

Good luck

---

### Post by justleen on 2007-03-20
what i used:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
(the dreator was VERY helpful, incase you get stuck)

backup tool:
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

freeware restoration tools:
[http://www.programurl.com/software/partition-recover-linux1.htm](http://www.programurl.com/software/partition-recover-linux1.htm)

---

### Post by jonathanapples on 2007-03-20
I just moved the disk to a spare windows machine and i can access the data ok - it just seems like ubuntu doesnt like the way that it was partitioned..?

---

### Post by justleen on 2007-03-20
ubuntu/*nix seems to be more "precise" when it comes to partitioning/partition tables. Windows just invents stuff allong the way (or something..there probably a perfectly reasonable technical explanation for this) . 
Though, i must say, when ubuntu gives errors like these, its a matter of time before windows will start to complain as well. Something is wrong, you just have the advantage of knowing it before it goes totally ********...

---

