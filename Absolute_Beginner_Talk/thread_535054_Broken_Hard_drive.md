---
title: "Broken Hard drive"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Controlpanel on 2007-08-26
Ok I deleted Ubuntu and am going to re download it sometime but what happened is when I deleted the partitions for it in my hard drive the space just went to unallocated space and I want to merge this space with my C: drive. How can I do this?

---

### Post by HappyGuy938 on 2007-08-26
> **Controlpanel said:**
> Ok I deleted Ubuntu and am going to re download it sometime but what happened is when I deleted the partitions for it in my hard drive the space just went to unallocated space and I want to merge this space with my C: drive. How can I do this?

Burn a copy of Parted Magic (the spiritual successor to GParted), or just apt-get GParted while running a LiveCD and use that to expand your NTFS partition to fill the space.  If you find your computer won't boot due to lack of a boot loader, create a Super Grub Boot Disk (Google it) and use that to restore the Windows boot-loader.  Alternatively, you could use a Windows XP install disk  to restore the boot-loader but I don't know anything about that method.

---

### Post by wormser on 2007-08-26
The title is a bit misleading.  It sounds like you are using Windows because of the C: drive.  If it is XP then go to control panel> administrative tools> disk management.  It is named something like that.  Then I would just format the drive and make it a D: instead of merging.

---

### Post by Controlpanel on 2007-08-26
Ok Can you tell me how to use the gparted live cd?

---

### Post by Controlpanel on 2007-08-26
...

---

