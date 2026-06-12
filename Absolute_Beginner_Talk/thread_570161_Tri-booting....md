---
title: "Tri-booting..."
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-10-07
I'd like to maybe tri-boot with Windows XP/Ubuntu/FreeBSD.  Right now, I have XP and Ubuntu on their own hard drives, and I would partition the Ubuntu drive and install FreeBSD there.  My question is, how would the bootloader work?  Would I chose not to install any bootloader at all when I install FreeBSD, and then would GRUB automatically detect it?  How would that work?

Thanks.

---

### Post by ryanVickers on 2007-10-07
Grub usually auto-detects stuff if they exist at the time of creating, but if you add stuff later, you will manually need to create an entry.  To do this, open /boot/grub/menu.lst and add one near the bottom - copy the windows one if your not sure how.  just change the name and "hd(x,y)" to being correct (x = hardrive number (0 = first, 1 = seconds, etc.) y = partition number (same deal as HDs))

---

