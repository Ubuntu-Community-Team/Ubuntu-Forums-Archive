---
title: "My USB Flashdisk isn't detected!"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by ozzie123 on 2005-07-06
Hello,

Did you guys know how to mount my USB drives? What should I type in the command line?

Thanks

---

### Post by defkewl on 2005-07-06
mount -t vfat /dev/sda1 /mnt/flash

but folder /mnt/flash must exist first :-D

---

### Post by ozzie123 on 2005-07-06
[QUOTE=defkewl]mount -t vfat /dev/sda1 /mnt/flash

but folder /mnt/flash must exist first :-D[/QUOTE]
 It said that special device /dev/sda1 doesn't exist. Hm... any other workaround?

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=defkewl]
but folder /mnt/flash must exist first :-D[/QUOTE]

to do that:

> sudo mkdir /media/flash

then 

> mount -t vfat /dev/sda1 /mnt/flash

now it should work.

---

### Post by N'Jal on 2005-07-06
Sometimes it doesn't auto detect my drive, try opening /media/flash and it often mounts mine then. Don't know why.

---

### Post by ozzie123 on 2005-07-07
There's no /dev/sda1 and there's also no /media/flash/

I've alread remount all with mount -a command but still not detected.

---

### Post by ozzie123 on 2005-07-07
Hey, I've did it! The problem is, the USB Flashdisk isn't detected as sda1, instead it detects simply as sda (withouth "1").

Now the problem is... how do I give a write permission to non-root?

---

### Post by Lord Illidan on 2005-07-07
Then try sda2, sda3 and so on....

---

### Post by N'Jal on 2005-07-07
i think it's chown, but don't know for sure

---

