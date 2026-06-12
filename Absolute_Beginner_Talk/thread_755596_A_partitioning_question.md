---
title: "A partitioning question"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by pandayanyan on 2008-04-15
So in all my Linux/Ubuntu endeavours I have come across a few questions about partitioning that maybe someone can answer for me. Now I am not an experienced user by any means and if anything am closer to newb level so forgive me in advance for whatever.

Ok so I was thinking I have 2 harddrives in my comp one labeled sda and the other shows as sdb or somethign of the like. can I have ubuntu / , swap, and /boot on sda and have all of sdb for /home? 

also if this is possible is it possible to have sda and sdb share space for a single partition like /home... example

SDA: 10 gb
/ = 2gb
swap = 4gb
/boot = 1gb
/home = 3gb

SDB: 10 gb
/home = 10 gb

Just curious....

---

### Post by Inxsible on 2008-04-15
i think your swap is way too big at 4gb. anything above 1gb of swap is a waste of space.

also you might need the root to be bigger than 2gb to install.

i dont think you can span the home partition across two physical drives. any partition has to be contiguous.

---

### Post by spiderbatdad on 2008-04-15
Home can and should be on a separate partition...IMO: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by bumanie on 2008-04-15
You really need at least 6g / probably 7g to make sure. swap of 1-2g is ample.You can have a separate /home, but it has to be one drive. My / files are usually in the vicinity of 5-6g. I don't believe ubuntu will install to / of 2g. The base system takes about 3.5g before any other programs/binaries are added.

---

### Post by cm.squared on 2008-04-15
Also /boot probably only needs to be 100 Mb or so.

---

### Post by pandayanyan on 2008-04-15
thanks all for your help . The example was only that (an example) my real values are much different. I just used that to try to explain what i was trying to ask.

Just so everyone knows it IS possible to put /home in a seperate partition. (i know cause i just reformatted my HD and did it just to see if I could. What i DONT know is if you can have /home on one harddrive and on another one at the same time. and if you can will it show as a single /home?

---

### Post by bodhi.zazen on 2008-04-15
Yes you can do this with LVM. The alternate install will allow your to configure LVM at the time of installation, otherwise you would have to do it post install and move /home.

Be prepared to read a little.

[http://howtoforge.com/linux_lvm](http://howtoforge.com/linux_lvm)

[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

---

### Post by barney385 on 2008-04-15
If it's set in a Raid0

---

### Post by pandayanyan on 2008-04-15
thanks allot. I originally partitioned with too little space for / so i reformatted and reinstalled /repartitioned last night with plenty of room and put /home on a seperate HD but i had a ton of unused space on the first one since all that was on there were system files and swap so i wanted to make it usable in case i needed it in the future. 

 DAMN... good thing i like to read ha ha thanks again!:)

---

