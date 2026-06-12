---
title: "I got a Serious Problem, PLEASE Help ME . . ."
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by IeU on 2006-04-24
Ok,

i downloaded the LIVECD 6.06 Ubuntu . . .
Played with it a bit and decided to install it on my hd . . .

so i went to windows and free 10gb using partition magic 8,
everything worked good, i boot and im in windows again with a 10gb less hd . . .

so i boot up ubuntu using the livecd,
and ran the install ( icon )
everything was going fine,
selected to manually partition my hd,

there i saw,
hda1 - windows - 142gb
unpartitioned space ~10gb

i selected the unpartitioned space and gave 5gb to / 4gb to /home and the rest to swap

so at the end i had something like this
hda1 - ntfs windows - 142gb
hda2 - ext3 - / - 5gb
hda3 - ext3 - /home - 4gb
and swap

everything seemed fine and i clicked next . . .

then i got the "15%" problem . . .
( [http://www.ubuntuforums.org/showthread.php?t=164109](http://www.ubuntuforums.org/showthread.php?t=164109) )

so, i waited about 15 mins, nothing happened, i closed that window and restarted thinking about formating the linux partitions using partition magic, so that maybe could avoid the 15% problem with the linux partition . . .

so,
windows didnt show up, was saying something like : disk/boot failure, insert a disk
( something like that .. .  )

then i said to myself : dang, ubuntu erased my mbr, no big issue, a fdisk mbr could solve the problem, or even in ubuntu i could solve this problem . . .

so i booted livecd, and just to check, i called to installation again . . .

and at my partition table seems like this now :

unpartitioned space = 160GB !

so where is my windows ?

what can i do ?

please help ! i CANNOT lose my data there :(:(:(

i did nothing wrong !!! help me please !

---

### Post by Sef on 2006-04-24
First, what happened is likely related to Partition Magic.   There are numerous threads on problems with it.

Second, to rescue your data if possible, here are 3 programs that you can download and burn:

[http://http://trinityhome.org/trk/]("http://http://trinityhome.org/trk/")

Note: Trinity can write to NTFS, though I don't know how well it works.

[http://www.ultimatebootcd.com/index.html]("http://www.ultimatebootcd.com/index.html")

[http://sysresccd.org/Main_Page]("http://sysresccd.org/Main_Page")

---

### Post by delta32 on 2006-04-24
It sounds like you messed up the partition tables. It *shouldn't* have formatted the whole drive so you should be able to recover the partitions. I've had this problem before and I was able to fix it by using a program called [testdisk](http://www.cgsecurity.org/wiki/TestDisk).

---

### Post by ykpaiha on 2006-04-24
try gpart as well very usefull to recover the hd crashs
[http://www.stud.uni-hannover.de/user/76201/gpart/](http://www.stud.uni-hannover.de/user/76201/gpart/)
it is actually the one who saved my hd life at least twice!!
do not forget to do everything under root =<sudo

""Guess PC disk partition table, find lost partitions
Gpart is a tool which tries to guess the primary partition table of a
PC-type disk in case the primary partition table in sector 0 is
damaged, incorrect or deleted.

It is also good at finding and listing the types, locations, and
sizes of inadvertently-deleted partitions, both primary and logical.
It gives you the information you need to manually re-create them
(using fdisk, cfdisk, sfdisk, etc.).

The guessed table can also be written to a file or (if you firmly
believe the guessed table is entirely correct) directly to a disk
device.""

this comes from synaptic comments***

---

### Post by gr0kzer0 on 2006-04-24
I haven't got anything helpful to add I'm afraid...

What I want to say is: in Usenet, a few ppl have been saying that the installer on the Dapper live cd has gone wrong and bombed their Windows.

Seems like there may be a problem there. I haven't used Dapper at all so I can't say from experience, just what I've read on Usenet. But maybe there's a bug?

---

