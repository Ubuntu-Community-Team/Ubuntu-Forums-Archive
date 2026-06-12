---
title: "two linux partitions?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2007-11-26
umm if i am doing two difrent linux distros do they both need to ahve root and swap with i think they do but just checking

---

### Post by Dr Small on 2007-11-26
They both need to have a Root, but you can use the same swap for both OSes, because the swap from one would not be used, because you can not run both at the same time.

---

### Post by lespaul_rentals on 2007-11-26
Distro 1 needs to have its own /, as well as Distro 2.

Distro 1 and Distro 2 can share /swap.

Distro 1 and Distro 2 can (usually) share /home.

---

### Post by fedex1993 on 2007-11-27
okay thats good i think i will just use 2 swap 2 homes and 2 roots one because the other distro is for my little cusin well not little just yoinger

---

### Post by teryowen on 2007-11-27
Use ONLY ONE swap partition, as its a waist of space to have 2.

---

### Post by Dr Small on 2007-11-27
> **teryowen said:**
> Use ONLY ONE swap partition, as its a waist of space to have 2.
+1
Otherwise, you are wasting alot of precious disc space.

---

### Post by mcduck on 2007-11-27
The only thing about using same swap partition for different Linux installs is that you cannot suspend one Linux and then boot to the other, as the suspend data is written into swap and booting the other install would overwrite the suspend data..

But as long as you don't need to use suspend-to-disk it's a good idea to use share the swap between Linux installs.

---

### Post by lespaul_rentals on 2007-11-27
Not only would having seperate /swaps be a waste of space, it would also be a waste of partitions.  You can only have so many.

---

### Post by Dr Small on 2007-11-27
I never use suspend, so that would not bother me any. :p

---

