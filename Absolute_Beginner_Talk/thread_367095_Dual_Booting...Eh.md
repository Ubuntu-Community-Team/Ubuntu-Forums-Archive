---
title: "Dual Booting...Eh?"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by t3h pwnage on 2007-02-21
I have been running windows on my computer all my life basically but im looking for a change. Windows has been ticking me off, mac is just worthless, and then theres linux...the holy grail of operating systems. Now your probably wondering where the dual booting...eh? title comes in, and here it is.  I would like to run linux on my new computer im building but i also want to run windows xp on it too.  I know you can split your hard drive and dual boot. But how in the name of ubuntu do you do it?:confused: :confused: :confused: 

[SIZE="1"]I have a friend who split his 100 gb for windows, 100 for linux, 100 for general stuff that is shared, and 20 for who knows what. I would like to do the same thing [/SIZE]

---

### Post by Eigenwert on 2007-02-21
Check out this here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
You'll probably want to partition the drive first, i.e. split it up into various sections for the different OS's. You can easily do that with an Ubuntu Live CD, just click on System > Administration > GNOME Partition Editor. Hope this gives you a starting point.

Good Luck!

EW

---

### Post by vigleik on 2007-02-21
Just install windows first, as windows likes to take the whole hard drive. Then you can shrink the windows partition and install ubuntu. Ubuntu will automatically recognize windows and add it to the grub menu. (I know there's a way around having windows nuke everything else on the computer, but this seems easier.)

---

### Post by r4ik on 2007-02-21
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by terdon on 2007-02-21
It's actually quite straihgtforward. Just remember to install windows first and to have it on the first partition of your first hard drive (C in windows, /dev/hda1 in linux or /dev/sda1 for scsi drives). 

After that, just boot with the ubuntu cdrom and follow the instructions. You will be asked to make a partition for your system (I agree it is better to have the partitions ready beforehand) and then the installation should give you a dual boot system with no problems.

Good luck!

---

### Post by Duck2006 on 2007-02-21
[http://video.google.ca/videoplay?docid=-6104490811311898236&q=dual-boot](http://video.google.ca/videoplay?docid=-6104490811311898236&q=dual-boot)

This may be of help

---

