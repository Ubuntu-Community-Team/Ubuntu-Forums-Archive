---
title: "boot partition"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by abijah on 2006-10-02
Is a separate boot partition (hda1, hda2, etc) really necessary on a Linux system?

Can I suffice with just a swap and "/" partition?

What advantages do I get with a separate boot partition?

---

### Post by xpod on 2006-10-02
You can have as many separate partitions as you want by all accounts.
A "/" and a "swap" are fine to start but you might end up wanting the separate home partition down the road.....
I`d just go with the basic setup to start with but these guy`s will help you have as many as you want im sure......IF you want them:D 

Good luck

---

### Post by sumguy231 on 2006-10-02
It's not required, and I don't use one personally. I strongly suggest a seperate home partition though.

---

### Post by anaconda on 2006-10-02
Separete boot partition is good IF you plan to delete ubuntu in the future, or you like to test different linux distributions.

If you delete your ubuntu, and dont have a separate boot partition your grub-boot loader stops working (because parti of it is in /boot), and you cant boot to your other operating systems any longer..
However, if you have a separate partition for boot this problem doesn't happen.

Good size for /boot partition is 100MB (which is actually quite big for /boot (less than 50MB would still be big enough..))

---

### Post by celsofaf on 2006-12-05
You could also install a small distro (like Damn Small Linux, or other) at /boot partition, for recovery pourposes, or even for fun. :)

---

