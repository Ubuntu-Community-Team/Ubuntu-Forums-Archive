---
title: "Partitioning for dual boot on a G4"
date: 2006-07-09
forum: Apple PPC Users
---

### Post by meshica7 on 2006-07-09
--------------------------------------------------------------------------------

 Hello Ubuntu Family!
1st of all,I had previously posted thius thread under the Absolute Begginer Talk folder but figured the response would be quicker here.
My name is Juan and I just recieved my copy of Ubuntu 6.06 LTS for Mac (I have a Power Mac running OS X 10.2.8.I have 4 HDs installed on my system and would like to use a partition on one of them in order to have a dual boot system.Is this possible?If it is,I am needing a little help with this. I have gotten as far as the partitioning prompt portion of the Ubuntu Install process but am afraid that I may erase everything (as the default insatll will do) completely off of my chosen drive. .I have tons of Pro Tools and graphics files on this drive and would just like to use the free space/partition.I have partitioned my drives before under OS X but I am not sure how to do it in this case :confused: .Can anyone help me out here?
Thanks folks.
BTW...this is my 1st post!
:D 
Juan R Leõn

My site with music and more...

Strada-Sphere Radio Podcast:Stick® Music and Nuthin' But!

---

### Post by ahaslam on 2006-07-09
Hi,

I have recently partitioned my drive without loosing any data, using [Gparted Live]("http://gparted.sourceforge.net/livecd.php").

Have a look & give it a try.

Tony.

---

### Post by meshica7 on 2006-07-09
Tony,
 Thanx for the info.Will this program run in OS X (PPC)? I keep reading a lot about C++.
Thanx!
 Juan

---

### Post by zachws on 2006-07-09
This will help you out:

[http://ubuntuforums.org/showthread.php?t=89960&highlight=parted+os](http://ubuntuforums.org/showthread.php?t=89960&highlight=parted+os)

That thread will show you how to repartition your drive (presently occupied with OS X) however you wish.

Some more tips (which may be overkill):
-Disable journaling in OS X before you repartition
-(obviously) boot from live cd
-get to parted by typing 'sudo parted' in terminal then type 'print' to see your present partitions and resize to, you guessed it, resize them.

---

### Post by meshica7 on 2006-07-09
Zach!

Thanx for the info!I visited the link and it looks very promising.I will give it a whirl and let ya know if I run into any snags.
:rolleyes: 
Juan

---

