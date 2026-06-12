---
title: "partion resize disaster!"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by bren on 2007-06-03
Hi o helpful ones.

Ok i was just enjoying Ubunto on my dual boot Win XP / Feisty laptop when I decided to use gparted Live Cd to increase the size of the FAT32 partition i am using for data (access from both OS's).

Unfortunately Gparted seems to have quit part way through 

Current situation
--------------------

[Laptop came with OEM recovery disks and not separate XP install disk.]

On booting Gparted Live CD again I have the following partitions

1) old win xp partition
39GB hda1 NTFS. Gparted now shows that this partition is empty. When i try to boot win it fails just after start. Gparted shows disk errors symbol

2) 10GB hda2 Ubuntu 3.53GB used. Ok and Ubunto boots OK. Left immediately to try and avoid overwriting anything I shouldnt.

3) 2GB hda3 linux swap partition (<1GB memory on my machine). Status Ok according Gparted

4) 23GB hda4 with error status. Was FAT32 with about 21GB of data on there. I have it all on DVD (except last few weeks which is only a few photos really)

5) 19 GB unallocated

So any suggestions on what I should try?

I can get back to where I was by

a) using OEM recovery to get fresh win xp install
b) adding data from DVD
c) reinstalling Ubunto etc

But hoping for a short cut!

cheers
bren

---

### Post by meng on 2007-06-03
Firstly, you're very lucky you backed up your data. Condolences on any lost photos, but at least you have most of your data, and that's great.
Secondly, make sure you don't use anything except a LiveCD for the time being.
Thirdly, consider downloading System Rescue CD (on another computer of course) and running it as a LiveCd. It has some tools for looking at and fixing your partition table - sfdisk and test-disk I believe may help you.
I am NOT a partition recovery expert by the way, so listen to other opinions.

---

### Post by bren on 2007-06-03
meng

thanks for the advice

will download these tools you mention via my work computer and see what gives....

bren

---

### Post by bren on 2007-06-04
meng and others
thanks for you help
prob solved
see [http://ubuntuforums.org/showthread.php?t=463584&highlight=bren](http://ubuntuforums.org/showthread.php?t=463584&highlight=bren) 
for more details

bren

---

