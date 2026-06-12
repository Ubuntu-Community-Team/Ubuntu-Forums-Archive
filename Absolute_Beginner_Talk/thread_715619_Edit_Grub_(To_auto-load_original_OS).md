---
title: "Edit Grub? (To auto-load original OS)"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Xarok on 2008-03-05
So I'm Running Ubuntu 6.10 on an iBook G4.

I use OSX more often so it would be nice if Grub auto-loaded it instead of Ubuntu.

How can I do this?

Thanks guys

---

### Post by kpkeerthi on 2008-03-05
Look for the line that says **default 0** and change the index to point to the OS you want it to auto-boot. If OSX is the second entry in GRUB change the line to **default 1**

Or post the contents of /boot/grub/menu.lst and I'll assist you.

---

### Post by Xarok on 2008-03-05
> **kpkeerthi said:**
> Look for the line that says **default 0** and change the index to point to the OS you want it to auto-boot. If OSX is the second entry in GRUB change the line to **default 1**

Or post the contents of /boot/grub/menu.lst and I'll assist you.

It seems that there is no Grub directory in /boot/

---

### Post by kesman on 2008-03-05
it's grub, not Grub. Linux is case-sensitive.

---

### Post by Xarok on 2008-03-05
> **kesman said:**
> it's grub, not Grub. Linux is case-sensitive.

I had gone to the boot directory and done an ls

---

