---
title: "which to install first? ubuntu or xp"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by BlueLava on 2006-10-29
My girlfriend has just purchased a new hard drive and a copy of xp. she wants me to put the new hard drive into my computer and install xp on it. the problem is, i want to keep my original hard drive with ubuntu on it. is there a way i can do this and run both on separate hard drives and if so which do i install first? i have backed up all my data so i can start from scratch.

---

### Post by WalmartSniperLX on 2006-10-29
Oh I see, you're doing 2 hdds. 

:mad:  I would like to know how to do this too since I also have 2 HDDs and later want to dual boot vista

---

### Post by aysiu on 2006-10-29
Well, you're supposed to install XP first, but you can just install it on that drive and then reinstall Grub to the MBR, which will automatically detect and add XP to the boot menu.

---

### Post by mahy on 2006-10-29
I'd say put the new drive in there, set it as the primary master, install xp on it and then boot some ubuntu live cd, mount the ubuntu partiton, chroot into it, run 'grub-install hd0' and adjust /boot/grub/menu.lst appropriately, should the need arise.

---

### Post by BlueLava on 2006-10-29
thanks guys, i'll give it a go.

---

### Post by gn2 on 2006-10-29
Here you go: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

