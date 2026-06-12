---
title: "Partition"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by tomco on 2007-02-18
Help! I have tried experimenting with SUSE etc. in the past but was always put of by the impenetrable unfamiliarity of the terms used and lack of 'windows' translation (sorry) to help me identiify with it to begin with. However, having stumbled upon both Puppy Linux and Ubuntu I am excited at the possibility of ultimately porting completely over to Linux. So, having tried the live desktop I decided to go for the full install - and it went a dream, or so I thought! I selected to manually partition (I have done this before in Windows and wanted to specify the where and size of the partition). I have two 160g HD's (the first for system and the other 'D' for files etc.) I set up, on the 'D', two partitions - one for '\' and the other for 'swap' and selected these accordingly when asked which partitions I wished to use. Heres the confession - I did get a box asking me about the 'D' and its role (obviously my words) and if I wanted to ignore to continue - which I did!. Its now dissapeared completely - from both Umbuntu and Windows! I know enough to know that its not actually gone but cannot now get to it. As yet I do not have internet on Umbunto (wireless connection - a post for another day) so went back to windows to install Partition manager (I dont know Linux enough to understand an alternative yet) but my Installer has gone and so I cannot install PM - and guess what - I have one of those PC's without a floppy as well! 

Sorry this has been a long rambling post but I need to get my 'D' back! Any ideas? I know for sure I didn't touch my system Partition when installing so cannot imagine how this happened

---

### Post by laidback on 2007-02-18
Oh dear. Your experience is much the same as my own, eventually arriving at Ubuntu's door having looked inside many others. I assure you that it's great.

My suggestion is to boot the Live CD of Ubuntu and then run Gparted (note spelling). I think it's on one of the menus, probably System>Administration then it's called Gnome partition editor. Now this little beauty will allow you to examine your hdd's without them being mounted. (you may already know about mounting devices) The idea is to see whether both your hdd's are listed in the drop down menu top right, and whether Gparted reports on them as you would expect. 

For the naughty D drive (which will not be called D by the way, but something like /dev/hdb) you can examine the partitions it has. Now I'm not saying that this is necessarily the place to cure any ills, but it may give you some more info. If D doesn't appear then there is a problem, one that I probably can't help you with, apart from suggesting a reformat, which can be done in Gparted.

It's a start. Be careful not to do further damage to your hdd's with Gparted, although it's quite friendly so you'll have to be quite determined to make silly mistakes.

---

### Post by ieee488 on 2007-02-18
D:\ has "disappeared" because Windows cannot see the Linux filesystem.
Try installing this free program [http://www.fs-driver.org/](http://www.fs-driver.org/) to be able to see the ext2 filesystem.


Linux does not use C:\, D:\, whatever.
It generally refers to the physical hard drives as  /dev/hda ,  /dev/hdb,  etc.

If your hard drives are PATA, then Linux most likely sees your C:\  as  /dev/hda
and your old D:\ drive as  /dev/hdb.

---

