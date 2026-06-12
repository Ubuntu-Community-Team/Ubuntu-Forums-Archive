---
title: "Scandisk"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by j002 on 2006-12-14
Every now and then my computer freezes, sometimes after the HD goes "tunk", and I have to hard reset.

I think it might be the HD because a power supply I changed there was this smell of nail polish and the chip on the top is charred a bit.

Is there any equivalent of scandisk on Gnome, I can't find anything ?

---

### Post by Shatrat on 2006-12-14
There is a program called fsck (File System ChecK) which scans and repairs filesystems but you're not supposed to run it on mounted drives or it could eat opened files.  I believe the best way to do this is to boot the live CD and run it on the unmounted hard drive.
I just checked and you can force a fsck on next reboot if you make a file in the root directory called forcefsck (Force F*ck? who names this crap)
Basically;
cd /
sudo touch /forcefsck

Then reboot and the init scripts will see that and know to scan the filesystem.

---

### Post by wpshooter on 2006-12-14
> **j002 said:**
> Every now and then my computer freezes, sometimes after the HD goes "tunk", and I have to hard reset.

I think it might be the HD because a power supply I changed there was this smell of nail polish and the chip on the top is charred a bit.

Is there any equivalent of scandisk on Gnome, I can't find anything ?

Am I missing something here ?

When you say the hard drive goes "tunk", do you mean it is making a sound just before the system freezes ?

If your hard drive has a physical defect, running scandisk is not going to fix it.

If you suspect your hard drive is going bad, you need to get the hard drive manufactuers diagnostic software and check the integrity of the hard drive.

Good luck.

---

### Post by moshuptrail on 2006-12-14
open terminal and type: dmesg

what do you see?

if you have bad blocks you will see errors

---

