---
title: "Dual-boot with Xubuntu 6.06 and Windows XP"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by Xanthus on 2006-06-27
I would like to dual-boot from two seperate hard-drives either XP or Xubuntu.  I've found that niether will recognize the other and the only way I can choose is by manually switching the drives to Primary drive 0.  If anybody could help me it would be greatly appreciated.

---

### Post by jrd on 2006-06-27
> niether will recognize the other
What exactly do you mean? How do you have everything set up?

---

### Post by verbatim210 on 2006-06-27
install windows first
second install linux

the linux installer has a boot menu thingy called grub, that'll fix you up!

---

### Post by confused57 on 2006-06-27
You might want to take a look at this guide:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

It should just be a matter of connecting your Ubuntu drive as the master and Windows drive as the slave...then editing your /boot/grub/menu.lst by making an entry to boot Windows from the Ubuntu grub.

---

