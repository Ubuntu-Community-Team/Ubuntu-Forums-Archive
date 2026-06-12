---
title: "Need help with installation of 6.10"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Thrasonic on 2007-02-25
Hey all, 

I've tried twice now to install Ubuntu from the Live CD (6.10) and it hangs up  at around 50% copying files.  The way I have the hardware setup is as follows:

I have a SATAII drive partitioned with Windows XP and I added a PATA drive (40GB) to the mix specifically for this Ubuntu install.  Both times I tried installing Ubuntu I did it the "easy" way and let Ubuntu choose how to setup that 40GB drive.  It seems things are going fine but than it just sits at 51% for hours.  I let it run over night for about 8 or 9 hours and it hadn't moved beyond 51% in that time.  I also noticed that the hard drive light wasn't flashing so I'm assuming nothing was happening that whole time.

I'm trying to figure out if I should try using 6.06 or if I should choose to manually partition the 40GB drive or what.  I don't know if manually choosing to partition the drive will make a difference because it seems like the install gets past that part (there's actually no message that says anything about the install creating partitions or something... it just goes straight to copying files).

I've looked in Windows Disk Management and I see the two partitions that the installation apparently created.  One is "Active" and is about 36GB.  The other is "Healthy (Unknown Partition) and is about 1.5GB.  They don't show up in My Computer, but they are visible in Disk Manager.  So it looks like the paritioning is happening but the install gets stuck on copying files.

Any thoughts?

---

### Post by raja on 2007-02-25
I assume you have checked the install cd. Sometimes using the alternate cd (with text-based installation) may solve problems. I prefer to do the partitioning myself usually. If you are not sure if the partitioning is done right, you can also use a separate live cd (like system rescue cd or gparted live cd) to do that. 
Just some thoughts.

---

### Post by jvc26 on 2007-02-25
My suggestion would be to first check the .md5 of the downloaded iso (if you downloaded it) then run the disk check. If they both come up fine, it may just be the livecd not working greatly with your setup, you can also use the Alternate CD - which I use all the time now as if you're sure about installing it its not a problematic method.
Il

---

### Post by Thrasonic on 2007-02-25
Where do I get the alternate CD?

---

### Post by jvc26 on 2007-02-25
Same download page as the livecd. (ubuntu.com?)
Il

---

### Post by Thrasonic on 2007-02-25
Would using the DVD download be any better?  And how do you check the md5?

---

### Post by jvc26 on 2007-02-25
To check the md5 I'd have a look at:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
Under the bit about md5 checking.
Il

---

