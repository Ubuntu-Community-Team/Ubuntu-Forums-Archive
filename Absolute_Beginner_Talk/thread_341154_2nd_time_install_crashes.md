---
title: "2nd time install crashes"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by dmj1973 on 2007-01-18
Can someone please help me ?

I am REEEEALY stuck. 

I removed the XP partitions with a partioning tool, then I installed Ubuntu desktop without a problem. I then ran it for a few days with no errors issues or anything ! Then I decided I would like to look at the Server version. I removed the partions created by the Desktop version with a partitioning tool and installed server version, whcich again ran fine, btu i didn't like it. So and this is where I now have a problem.

I removed the partitions and ran the live cd selected install and repeated the process for installing ubuntu desktop in the same way as i did the 1st time. It gets to 51% of the way through the install and then just freezes. The time estimate goes up and up and up, and i have left for 24hrs+ and nothing finishes.

ok i tried a new copy of the cd and that did the same. 

i have tested the drive and memory and XP re-installs and runs without issue. Can some please help me get UBUNTU desktop back on this machine ?

Thanks
Dave

---

### Post by jvc26 on 2007-01-18
I would advise running the disk check on that disk - when you put it in and boot to the cd, select the disk check - it may well be a problem with the burn (you may have burnt at too high a burn speed) Also check the md5sum of the .iso you downloaded - if that is incorrect then you will need to re-download and thats whats causing you problems - I'm surprised as it worked the first time, but its not unheard of.
Il

---

### Post by dmj1973 on 2007-01-18
hi,

thanks, I did do a disk check and it came back and said all was ok.

Forgive me but how do i check the md5Sum ?

Dave

---

### Post by Josh1 on 2007-01-18
Try running the gparted live cd (the livecd is like ~25 megs) then see if there is more then 1 partition for that disk.

GParted - [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by jvc26 on 2007-01-18
No worries mate, to do the md5 checksum follow the instructions on md5 on here:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
Il

---

