---
title: "Partitioning SATA and IDE for dual boot"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by JNasci7906 on 2006-06-15
hey guys and gals, ive been scouring the forums the last couple of days for an answer to my problems, but unfortunately, i havent found one (or am too stupid to realize it). My problem is that I want to dual boot my machine to run ubuntu and XP (for gaming, i hate wine). However, when i installed breezy i formatted my whole 80 gig harddrive for it. 
Questions: 
Is there a way to repartition my HDD (about 70 gigs left) so that 30 gigs of it can be used to install windows? I have Gparted, but dont understand how it works.

Also, i have some other drives laying around, however, there seems to be a problem with my main SATA drive, and the other IDE drives, i cant get the master/slave combination right.

I should also mention the other hard drives are from several Xbox's and I cant get them to be recognized by either the ubuntu or winXP installs....any help with a program that can detect and just clean them up would be of great help.

thanks in advance for the help all

Nash

---

### Post by Sandlst on 2006-06-15
I can't help you with the xbox drives, but it would be helpful if you could copy the contents of your fstab file ```
gedit fstab
``` and paste it in here, then we might be able to give you step by step directions on how to use gparted to make the changes you want.

---

### Post by JNasci7906 on 2006-06-15
when i typed that in it took me to an empty/blank document......uh oh??

---

### Post by confused57 on 2006-06-15
Try:
```
cat /etc/fstab
```

this will display the contents, without being able to modify.

If you wanted to modify:
```
sudo gedit /etc/fstab
```

Edit:  These may not work with the live cd.

Are your drives recognized in your bios?

---

### Post by Sandlst on 2006-06-15
Ooops, my bad on fstab, also you probably will have to use a livecd to make changes to the partition, the new dapper Desktop CD can do this (with gparted) if you don't have one.

---

