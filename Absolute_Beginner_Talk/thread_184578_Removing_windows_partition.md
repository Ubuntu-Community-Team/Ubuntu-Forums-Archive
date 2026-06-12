---
title: "Removing windows partition"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by NyTE on 2006-05-30
Hello.Is their a way to remove my windows partition and adding that space to my ubuntu partition?

---

### Post by macdo on 2006-05-30
Boot with a livecd and use the partitioning tool (I think it's called Gparted).

Remember to back up first, before you do any partitioning!

---

### Post by mostwanted on 2006-05-30
Or you can just sudo apt-get install gparted and do it from your installed system.

---

### Post by aysiu on 2006-05-30
If your Windows drive is before your Ubuntu drive, you can't just add it on to the Ubuntu drive. You can add space to the *end* of a partition but not to the *beginning* of it.

For example, if Windows is /dev/hda1, and Ubuntu is /dev/hda2, the best you can do is make Windows into a separate data partition. Or... make it a new /home partition:

[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

If, however, Ubuntu is /dev/hda1 and Windows /dev/hda2, you can just delete the Windows partition with GParted and add the freed-up space to Ubuntu. You will need a live CD for this, however.

---

### Post by zolookas on 2006-05-30
[QUOTE=aysiu]If your Windows drive is before your Ubuntu drive, you can't just add it on to the Ubuntu drive. You can add space to the *end* of a partition but not to the *beginning* of it.[/QUOTE]
It's possible using Partition Magic, but partition magic will move your data to the beggining of your extended partition so it may took few hours. If you still have windows, download Partition Magic trial version ( [http://www.soft32.com/download_151.html](http://www.soft32.com/download_151.html) ) and make emergency floppies (you'll need 2 floppies). Then boot from first floppy and insert second when prompted. Start partition magic, delete your windows partition and resize your linux partition.

---

### Post by NyTE on 2006-05-30
Alright got it going,thanks.

---

