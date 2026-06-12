---
title: "GRUB broken after power failure, &quot;find /boot/grub/stage1&quot; returns no devices :( help!"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by ijason on 2008-04-20
hey there. 

i'm having some trouble with GRUB being severely broken on my machine. after a power outage, the system boots through the CMOS and hardware initializing screens, and then spits out a big fat "GRUB" after verifying the DMI pool. and that's it. no error code, no further information, simply "GRUB"

i've booted off a live cd, with the intent of reinstalling the GRUB, but ran into a snag when the "find /boot/grub/stage1" command returned no devices. it actually returned "/boot/grub/stage1", but no hd0(1) or anything like i would have expected. 

figuring that this may be because my hard drive isn't mounted after booting off the live cd, i tried to mount the drive, but - of course - root account is deactivated in the dang live cd so i can't mount the drive! 

what should i do from here?!

---

### Post by mgranet on 2008-04-20
You might try Super GRUB.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I feel your pain. Every time the power goes out, I cringe when I start up my comp for the first time. In the future, you might try a backup or ghost software that backs up your MBR. I use CloneZilla, which can be had as a LiveCD.

---

### Post by ijason on 2008-04-20
update : i booted off the system rescue disk from partimage's website, which gave me unfettered ability to actually mount the HD i was booting off of. and the "find /boot/grub/stage1" returned hd(0,0) for me. so i followed the usual 

grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0,0)

steps, and it looked like it installed correctly, but after rebooting i get the exact same GRUB error :(

---

### Post by ToSsMaStR on 2008-04-20
lol u guyz live in south africa by any chance?

---

### Post by ijason on 2008-04-20
**@mgranet** : ah! supergrub fixed it all for me, brilliant!

---

