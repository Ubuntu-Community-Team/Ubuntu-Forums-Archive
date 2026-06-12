---
title: "dual boot Windows XP extremely slow"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by jubilee0824 on 2007-07-06
I have a Windows XP laptop, and installed Ubuntu as dual boot. I've been using Ubuntu (first 6.10 then updated to 7.04) for few months now, and everything is fine on Ubuntu. But since I installed Ubuntu, Windows XP becomes exremely slow.

Upto "login" screen is fine, then it takes forever to load the task bar, and it even takes more than 5 minutes to start an application like firefox. It seems like Hard Disk performance has dropped significantly on Windows, but the same HDD works just fine on Ubuntu.

Also, I often get "Check disk needed for NTFS consistency" and have to run chkdsk /f when loading Windows XP. So I'm guessing something went wrong during resizing partitions during Ubuntu installation. Any idea to confirm/fix this will be appreciated. Thanks.

---

### Post by swoll1980 on 2007-07-06
how much hd space do you have on your xp partition?

---

### Post by jubilee0824 on 2007-07-06
it still has 3GB, about 15% of the 20GB C: drive. i know its not too much, but shouldnt be making the system sooo slow.

---

### Post by arif9k on 2007-07-06
do as i said

insert your xp setup cd into the cd drive  re-start

delete all the partition

make a partition which should be half of your  full hard disk.

then make a partition for c: which should be morethan 10gb.

run setup on c with ntfs

after sucessfull setup.

install your ubuntu.(partition with the option-use maximam free space).(dont resize the partition)

after sucess full installation of ubuntu restart.

boot up with xp, and it should work brezzy and breezy.

---

### Post by swoll1980 on 2007-07-06
I would think thats exacly the reason you should have at the very least 10gb per os and thats pushing it

---

### Post by swoll1980 on 2007-07-06
a 20gb hard drive is just not made for this type of installation

---

### Post by swoll1980 on 2007-07-06
> **arif9k said:**
> do as i said

insert your xp setup cd into the cd drive  re-start

delete all the partition

make a partition which should be half of your  full hard disk.

then make a partition for c: which should be morethan 10gb.

run setup on c with ntfs

after sucessfull setup.

install your ubuntu.(partition with the option-use maximam free space).(dont resize the partition)

after sucess full installation of ubuntu restart.

boot up with xp, and it should work brezzy and breezy.

If you do that your ubi won't wont run right it's a catch 22

---

### Post by jubilee0824 on 2007-07-06
my harddrive is actually 30GB, of which 20GB is for Windows, 10GB for Ubuntu.

i ran HD Tune to see the HDD speed, and the transfer rate becomes ridiculously slow (0.3-0.5MB/sec) after 35% and the access time is slow (39.2ms) as well....maybe my HDD is dying? but its funny Ubuntu still runs fast.

---

### Post by davidjmayo on 2007-07-06
> Also, I often get "Check disk needed for NTFS consistency" and have to run chkdsk /f when loading Windows XP. So I'm guessing something went wrong during resizing partitions during Ubuntu installation. Any idea to confirm/fix this will be appreciated. Thanks.


When you say install ubuntu do you mean again as in reinstall?

You didn't resize your NTFS (XP) partition did you??

If you did and didn't run defragment (in XP) before installing ubuntu......................

---

### Post by jubilee0824 on 2007-07-06
> **davidjmayo said:**
> When you say install ubuntu do you mean again as in reinstall?

You didn't resize your NTFS (XP) partition did you??

If you did and didn't run defragment (in XP) before installing ubuntu......................

things got slower after the first install of Ubuntu, which involved shrinking XP's NTFS partition, but i did't run defragment.....

---

### Post by davidjmayo on 2007-07-06
> things got slower after the first install of Ubuntu, which involved shrinking XP's NTFS partition, but i did't run defragment.....

Uh oh no defrag. Confirm-The resize has probably corrupted some of the partition. Not sure if there is a fix. If you have an XP CD boot from it and try the recovery if there is an option (sorry can't be more helpful I never used XP but I've heard it's somewhere but must be a full CD not a factory restore CD
DO NOT INSTALL XP OR DELETE THE PARTITION)

If that doesn't work try google or a windows forum for partition recovery

**Don't quote me on this** so wait a while for other replies. (Someone may know different)
I was reading a thread about this the other day but can't find it
I seem to remember the conclusion was get what data you can off the partition (unless you did a backup) and then  reformat and install XP again
Problem is this will affect your ubuntu boot menu (grub) but a search of this forum for "grub" no quotes will find the way to fix it.

EDIT:
1 I wasn't clear in my first post. You should defrag before resizing the partition not after if it reads that way
2 Still can't find that thread but this one has some recovery options in it see #4 [http://ubuntuforums.org/showthread.php?t=469897](http://ubuntuforums.org/showthread.php?t=469897)

---

### Post by jubilee0824 on 2007-07-09
thanks davidjmayo.

my C drive is severely fragmented (>25%), and defragment can't fix it. so probably i should have degragmented beforehand as you suggested...well i try the XP recovery process, i only have a Acer recovery CD, but i vaguely remember there was a way around to do the recovery process without a full XP CDROM.

---

### Post by ankel on 2008-06-04
I had the same problem. No exactly answers?

---

