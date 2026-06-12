---
title: "help!"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by senorgato333 on 2006-01-31
ok so i really want to use ubuntu! but i have windows XP on my hard drive and i want to use both at different times ive heard about partitioning how do i do this?!

thank you very much:D

---

### Post by carlosqueso on 2006-01-31
It's not hard at all....there are kind of two ways to do it.

1: The hard (but instructive and Ubuntu-only way)

Go into the installer, and select manually partition your hard drive.

Select your windows partition and make it smaller (you'll need a decent amount of space for ubuntu >7 gigs.

On the free space, create 2 new partitions: a ~1GB swap partition (choose swap) and the rest as "/" or "root" and formatted as ext 3.  

Then you'll be good to go with the install.

2) the easier, but needing more stuff way.

Download mandriva [www.mandriva.com](www.mandriva.com) and use their DiskDrake installer to partition your drive, then install Ubuntu over the linux partitions.   

Either one works, and I'm not one to say which is better.

---

### Post by asinsh on 2006-01-31
carlosqueso is right, it's easy to use the ubuntu installation disk to do all this for you.  But make sure to back up whatever you care about in your XP setup to another disk just in case.  When I first tried installing ubuntu as a dual boot as a complete newbie (yesterday), I messed up and killed my XP installation and had to reinstall.  My own stupid error and when I did it a second time I was fine.  But since you are a newbie at this, definitely make a backup even though it's simple and hard to make a mistake (since we newbies have an ingenious way of finding ways to make mistakes that noone else would have anticipated ;) .

You should also look for one of the many many installation guides floating around out there.

---

### Post by asinsh on 2006-01-31
Here's a guide that should help: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by aysiu on 2006-01-31
See the fifth link of my signature.

---

### Post by lreyes6 on 2006-01-31
hi
[LIST]
[*]First u need to make a backup of your full backup from you sistem
[*]then make an ext3 partition on your windows (more than 1Gb)
[*]then put the install cd and install ubuntu on that partition (do not touch the fat or ntfs that will harm your windows
[/LIST]

that was a few steps but for a complete guide you can read [this]("https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28boot%29%7C%28dual%29")

hope this helps

---

