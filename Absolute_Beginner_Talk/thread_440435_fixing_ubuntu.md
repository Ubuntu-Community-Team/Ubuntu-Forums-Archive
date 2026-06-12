---
title: "fixing ubuntu"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by em11488 on 2007-05-11
I think something is crazy wrong with my system. Ubuntu doesnt recognize my ntfs drive that I run vista on. Whenever Im in the terminal and I do something requiring a pw, mine doesnt work. and yes Im positive Im using the right pw and its not on caps lock. Vista crashes a lot, and ubuntu starts nearly 1 in every 10 attempts. Is there something wrong with my hd? Should i reinstall ubuntu, but if i need to do that, wouldnt that mess up the gub menu. please help

---

### Post by em11488 on 2007-05-11
and Im using 7.04 amd 64
my system
hp dv6000z
amd g4 x2 2.0 ghs
geforce 7200

---

### Post by Foxmike on 2007-05-11
Firstly, it would help a lot if you post the error messages the terminal gives you when the errors arrives (as for pw in examble).  By the way, note that when a password is required when using sudo, it is your password (not root password) required.

Having something wrong with your HD is one possibility as Vista crashes as well.  If you re-install ubuntu, you shouldn't be worried with MBR, as it will re-install GRUB (the bootloader) as well and will re-detect your Windows installation.

By the way, did you activate the NTFS support?

Regards,

-FM

---

### Post by ghostboy on 2007-05-11
> **em11488 said:**
> I think something is crazy wrong with my system. Ubuntu doesnt recognize my ntfs drive that I run vista on. Whenever Im in the terminal and I do something requiring a pw, mine doesnt work. and yes Im positive Im using the right pw and its not on caps lock. Vista crashes a lot, and ubuntu starts nearly 1 in every 10 attempts. Is there something wrong with my hd? Should i reinstall ubuntu, but if i need to do that, wouldnt that mess up the gub menu. please help

Are you going to move from Vista to Ubuntu completely?  It sounds like something got meesed up on the installation.  I would suggest reinstalling if you can.  If you reinstall use the LiveCD and use the repair installation option.  Hope that helps.

---

