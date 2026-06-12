---
title: "XP to Ubuntu, file transfer query"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by NvidiaN on 2008-01-29
I'm finally ready to switch from Windows XP to Ubuntu (7.10), but I'm a bit apprehensive. The reason for this is that I don't know how transferring files will work.

Once I install Ubuntu, how does one take XP files and move them into Ubuntu, that I may delete XP? I'm only working with one hard drive here, in my laptop, so I'm not really able to just put it all on some second computer and go from there.

Thoughts?

---

### Post by fiddledd on 2008-01-29
If it was me I would do the following:

1) Backup all important data onto removable media (USB HDD, Memory Stick, DVD etc)
2) Defragment XP
3) Install Ubuntu and Dual boot with XP
 here's a guide for that :[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

4) Then Dual Boot until I was certain I no longer wanted/needed XP

When you dual boot Ubuntu will mount your Windows Partition(s) and you can just copy paste to your Home folder.

BTW you could just search these forums for Dual Boot Xp for guides also.

---

### Post by aeiah on 2008-01-29
basically when you dual boot windows and ubuntu, you're installing ubuntu to different partitions (at least a root partition, maybe a seperate one for home). in ubuntu you'll also be able to see your windows partition, and be able to access the files. you can drag what you want across to ubuntu home (as mentioned), or continue working with them in your windows partition (if you install ntfs-3g so you can write to ntfs). it is good practice to move them across to your home folder through, or into a FAT formatted shared partition if you have hard drive space, which both windows and ubuntu can access. later on you can remove the windows partition, or format it and use it just for storage etc.

---

### Post by billgoldberg on 2008-01-29
Ubuntu gutsy gibbon can access the windows xp partition out of the box.

Open you home folder and search for it in the left menu.

---

