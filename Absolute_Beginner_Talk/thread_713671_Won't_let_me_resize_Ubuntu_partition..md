---
title: "Won't let me resize Ubuntu partition."
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by merschdawg06 on 2008-03-03
Hi, I installed Ubuntu with duel boot with Windows XP.  I wanted to use the swap partition and combine it with my Ubuntu partition.  I used Gparted to change the "swap" partition to "free space".  However, Gparted doesn't give me the option to resize the Ubuntu partition to it can use the extra space provided by the swap partition.  I don't want to risk playing around with Gparted because I know firsthand the havoc it can bring.  Any ideas?

---

### Post by smartboyathome on 2008-03-03
What version of Ubuntu are you using? Older versions of Ubuntu contain GParted 0.25, which doen't support what you are trying to do. Gutsy does, though.

---

### Post by merschdawg06 on 2008-03-03
I'm using Ubuntu 7.10.  Also, I'm not a pro at partitioning so if someone could explain the difference between a "primary" and "extended" partition that would be much appreciated.  I've got a sneaking suspicion that might be the problem...but I really don't know.

---

### Post by smartboyathome on 2008-03-03
I have a suspicion that your swap is under an extended partition? If so, you have to delete the extended partition and then you can add it to your ubuntu partition.

---

### Post by merschdawg06 on 2008-03-03
After doing some some more in depth look into GParted I found that my Ubuntu partition is an Extended partition.  Is that a problem?  If so how would I fix it without erasing my entire Ubuntu partition?

---

### Post by Gepetto on 2008-03-03
I'm pretty sure you can't actually resize partitions with GParted in Ubuntu, you have to get the bootable iso program thingy

---

