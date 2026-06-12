---
title: "Am I installing Ubuntu correctly?"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by fiver22 on 2006-07-24
I want to dual boot Windows and Ubuntu so I'm booting into Gparted: after my Windows partition I'll be creating a 5Gig ext3 partition, followed by a 1Gig Linux swap partition, and then creating another ext3 partition with the rest of the available space. 
   Then I'm going  to put in the the Ubuntu install CD and reboot: I'm assuming it will ask me which partition I'll be installing to -is that correct, are the partitions named so that I can see which is the right one to install to? -Once it's installed onto the correct partition and I reboot will I automatically be asked if I want to boot Windows or Ubuntu? -or is there something else I need to do so I can dual boot.
Thanks so much for any help -I appreciate it.
(I hope I was able to explain that properly -tell me if I can clarify anything: I'm completely new to this but I'm willing to learn)

---

### Post by userundefine on 2006-07-24
Make your 5G ext3 partition "root" (or "/" as it may be in the installer -- it's been a while since I saw it).

Then your second partition "Linux swap" as you said.

Then your third partition "/home", where your personal files will go.

Then the base system will be installed and you'll reboot to see Grub, and you can select either Ubuntu or Windows to boot into.

Should be good to go.

---

### Post by tzulberti on 2006-07-24
There is no need to format the disk and then restart. The installer has a partitioner GUI in step 3. The basics steps are:
1) Introducion of the installer
2) Time zone
3) Partitions
4) Which partitions use for each thing
5) Create user.
6) Review of the chosen things, and the last step to cancell instalation

It would automatically install grub, which would detect your windows instaled, and will let you chose which one you shoul boot.

---

### Post by Sef on 2006-07-24
Here's an excellent tutorial on [dual booting.]("http://users.bigpond.net.au/hermanzone/")

---

### Post by aysiu on 2006-07-24
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by gigaferz on 2006-07-24
[http://www.ubuntuforums.org/showthread.php?t=220226](http://www.ubuntuforums.org/showthread.php?t=220226)

Make the root as big as possible...especially if you  ever get automatix...

---

