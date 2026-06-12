---
title: "Non-system disk or disk error"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by pmc255 on 2008-01-17
I got a used laptop from work, and it was wiped clean with no OS when I received it.

I first installed Windows 2000 on it, but then decided to install Ubuntu. Now, when I start the laptop, it gives me the "non-system disk or disk error" message. Doing a reboot boots into GRUB and loads Ubuntu fine.

It seems to me that something's wrong with the MBR, but I can't find a way to fix it. Any ideas?

---

### Post by cecure on 2008-01-17
Could you please post the output of the following commands, run from a terminal in ubuntu.

```
sudo fdisk -l
```

```
cat /boot/grub/menu.lst
```

And to clarify, you need to turn on your computer twice in a row to boot grub?

---

