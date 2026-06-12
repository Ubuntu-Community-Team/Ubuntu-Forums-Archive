---
title: "USB Storage"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-06-16
I want to ruse the backup application to egularly backup my computer to a USB storage device.

I'm looking at this:  Beyond Micro / Mobile / 250GB / 7200 / 8MB / USB 2.0 / External Hard Drive

Does anyone know if this will work with Ubuntu? 
Or... Which USB device(s) have you had success with?

---

### Post by starcraft.man on 2007-06-16
> **RichPicker said:**
> I want to ruse the backup application to egularly backup my computer to a USB storage device.

I'm looking at this:  Beyond Micro / Mobile / 250GB / 7200 / 8MB / USB 2.0 / External Hard Drive

Does anyone know if this will work with Ubuntu? 
Or... Which USB device(s) have you had success with?

Any USB mass storage device should work with Ubuntu. The USB drivers work fine, mine works and I never bought it for Ubuntu. What you want to be concerned with when you get it later is what file system is on it. If its NTFS and your never gonna use windows with it, you might want to reformat it with Ext3 via gparted. Mine was fat32 which will work fine, but its not the greatest FS you know...

So sounds fine with making that purchase, hope your getting a good deal.

---

### Post by Angry penguin on 2007-06-16
I havent found a usb mass storage device yet that doesn't work with ubuntu. I currently have a 500gb WD mybook, a 128mb lexar thumbdrive, and a cruzer mini 128mb thumbdrive, they all work perfectly. The thumbdrives are fat32 formatted and the mybook is ntfs (read/write via ntfs-3g).

---

### Post by silkstone on 2007-06-16
As starcraft.man says, any USB drive should work - I've not yet found one that won't. I'd use FAT32 for sharing files with Windows or Mac, but it's not the best and also limits you to 4GB file size. (OK except for larger disk images.)

---

### Post by RichPicker on 2007-06-16
85 Usd

---

