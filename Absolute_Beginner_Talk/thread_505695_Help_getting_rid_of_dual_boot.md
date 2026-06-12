---
title: "Help getting rid of dual boot"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by gruesome on 2007-07-20
Bit of a newbie here..

Here's my scenario. I have 2 200gb SATA's. One with Vista and the other with feisty. Well i'm pretty sick of Vista all together so i want to get rid of it. I tried just unplugging the Vista HD and plugging the ubuntu drive into the sata1 port but that didn't work. So then i tried editing /boot/grub/menu.lst and changing the hd1,0 in front of Ubuntu to hd0,0 i unplugged the vista drive plugged the ubuntu drive into the sata1 port and that didn't work. How can i get rid of vista and just boot from my ubuntu drive?

---

### Post by ddrichardson on 2007-07-20
Put the drives in their original positions then remove the Vista boot entry from menu.lst. Once you've booted back into Ubuntu you can reallocate the Vista drive to a mount point under Ubuntu.

---

### Post by gruesome on 2007-07-20
Ok how do i *reallocate the Vista drive to a mount point under Ubuntu*?

---

### Post by ddrichardson on 2007-07-20
Create an ext3 partiton on it using gparted. Ubuntu should pick it up as a new device, if it doesn't you'll need to add it to /etc/fstab.

---

### Post by annda on 2007-07-20
> **gruesome said:**
> Ok how do i *reallocate the Vista drive to a mount point under Ubuntu*?

```
sudo gparted
```

format the drive and assign a mount point like that /media/new_drive

---

