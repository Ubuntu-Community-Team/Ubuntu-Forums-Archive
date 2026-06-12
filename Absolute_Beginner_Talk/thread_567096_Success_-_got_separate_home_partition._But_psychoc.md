---
title: "Success - got separate home partition. But psychocats instructions need updating"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-10-04
Psychocats is a great resource no complaints here. But the create separate home partition instructions need updating else a real newbie will get major frustrations.

1. Neither knoppix or ubuntu livecd could resize my hda1. The option was greyed out in knoppix and the partitions had a lock in ubuntu.  Gparted live cd is much better for this job and its very quick.

2. My pc is old and ubuntu live runs like a tortoise whereas knoppix is the much faster.

3. The instructions then are damn good except using nano is very odd for a newbie.

4. No errors encountered creating new home folder on hda3 but on reboot I found that it had been created as root permissions so had to sudo chown -R philcb /home.

Now I'm well happy to reinstall at any time. Found this tip too.

---

### Post by n3tfury on 2007-10-04
i've always had some sort of small problem every time i tried a built in partitioner up until 7.04 and the gutsy beta which both worked fine.  i'm still keeping my gparted cd though, as it's fantastic.

---

### Post by mlentink on 2007-10-04
> **philinux said:**
> 3. The instructions then are damn good except using nano is very odd for a newbie.

:lol:
Try vi ....

---

### Post by philinux on 2007-10-04
Fortunately I checked that nano was available on knoppix live. But for some other newbie trying this the first either Gedit or Kedit are sufficient for pasting one line in fstab.

---

### Post by aysiu on 2007-10-04
I don't see how the instructions need updating. You had difficulty resizing partitions with Knoppix or Ubuntu, and I'm sorry about that, but that's an exception, not a consistent experience. I am not going to make it a general practice to tell Ubuntu users to download and burn the GParted CD just to resize a partition if Ubuntu already has a partitioning utility built into it.

I use *nano* in the instructions because it is universal (KDE, Gnome, Xfce, whatever), and I would not recommend an after-the-fact creating of a separate /home partition to someone how is uncomfortable using *nano*. It is a complex procedure that isn't for the faint of heart.

---

### Post by scrooge_74 on 2007-10-04
i have notice that if you run a live CD on an old system and you don't have a swap partition already in place the system tends to be sluggish

---

### Post by philinux on 2007-10-04
> **aysiu said:**
> I don't see how the instructions need updating. You had difficulty resizing partitions with Knoppix or Ubuntu, and I'm sorry about that, but that's an exception, not a consistent experience. I am not going to make it a general practice to tell Ubuntu users to download and burn the GParted CD just to resize a partition if Ubuntu already has a partitioning utility built into it.

I use *nano* in the instructions because it is universal (KDE, Gnome, Xfce, whatever), and I would not recommend an after-the-fact creating of a separate /home partition to someone how is uncomfortable using *nano*. It is a complex procedure that isn't for the faint of heart.

Thanks for reply in my OP I said "Great instructions no complaints" Its really god to have a sep home partition now I feel much more secure.

The ubuntu livecd, I ren gparted from the menu but it had a lock on the partitions. For future reference how would I unlock it. In knoppix the resize was greyed out and showed the hda1 as busy?

---

### Post by Niniel on 2007-10-04
I very recently used the Ubuntu 7.04 live CD to resize the NTFS partition on my computer's hd and to create EXT3 and Swap partitions in the freed-up space - no problems at all (using the Manual procedure). In fact, I'd say it's faster than I remember Partition Magic to be (last time I used it it was v4, so it could be faster now). I was very happy with the tool, and would recommend it to everyone.

---

### Post by notwen on 2007-10-04
> **philinux said:**
> Thanks for reply in my OP I said "Great instructions no complaints" Its really god to have a sep home partition now I feel much more secure.

The ubuntu livecd, I ren gparted from the menu but it had a lock on the partitions. For future reference how would I unlock it. In knoppix the resize was greyed out and showed the hda1 as busy?

Were the partitions mounted?  Opening GParted sometimes has tendencies to mount any available drive on the HDD.  You cannot resize/modify partitions while they are mounted. =]

---

### Post by philinux on 2007-10-04
No I unmounted them in both ubuntu and knoppix live and they were set to read/write.

---

