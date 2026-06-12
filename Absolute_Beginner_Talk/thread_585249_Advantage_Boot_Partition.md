---
title: "Advantage: Boot Partition?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-21
Looking at partition schemes and would like your opinions.
I'm Setting up my Linux partitions like this. 

/
Swap
Home


Is there any advantage in adding a Boot Partition ?

---

### Post by steve.horsley on 2007-10-21
None that I have ever managed to think of.

---

### Post by Eddie Wilson on 2007-10-21
I've heard some mention that if you triple or double boot you need one. I triple boot but I've never used a boot partition and I've never had any problems. So I really don't know.
Eddie

---

### Post by rsambuca on 2007-10-21
The only time you really might *need* to have a separate /boot partition is if you have XP on an internal drive, and linux distros on an external drive that is not always connected.

---

### Post by Orbital75 on 2007-10-21
Thanks.... Just wanted to make sure and see what everyone's experience was.

---

### Post by cfaulkner on 2007-10-21
Honestly, the only reason why you want to partition off your hard drive is for maximizing your speed.  In this day and age, it's not necessary.  But back in the old days of solaris 2.6, we had to make sure that we had partitions for everything /usr /opt /usr/bin  and these were across Raid arrays.  Basically, the only reason why you'd wanna do that is if you wanted to force the boot partition to the first part of the drive to make sure that boot up was quicker.  
[SIZE="5"]
My short answer[/SIZE]

Keep it Simple:  

/
Swap

---

