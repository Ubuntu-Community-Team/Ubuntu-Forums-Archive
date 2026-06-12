---
title: "Please please help with installing Ubuntu"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by amphyx on 2006-07-10
Hi,

I'm having a problem, and not sure how to proceed...

I have three HDD's -- 2 160GB in a RAID 0 configuration that has WinXP (SATA). I have a third HDD (200GB IDE) on PATA.

I put the Ubuntu Live disk in and it booted fine. I then start the install. I am able to select the 200GB drive and install the software. The install completes successfully.

On reboot, WinXP boots, not Ubuntu.

If I go into the BIOS and set the 200GB as the bootable disk, the Ubuntu OS boots up fine.

My question is, how do I get this to dual boot without going into the BIOS?  The install is obviously not installing the boot menu.

I even tried installing with the Alternate Ubuntu CD, same result.

Is there something I missed, or is this even possible?  I've been spending way too much time on something that shouldn't be this difficult....getting quite frustrated.

Any help is greatly appreciated!
Thanks!
Gary

---

### Post by nalmeth on 2006-07-10
If you're sure ubuntu installed successfully, this may help:

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by scxtt on 2006-07-10
i would think you can leave the ubuntu disk as the "boot disk" in your BIOS, then install grub to your ubuntu disk (the non-SATA non-RAID0 disk) ... after you've got grub booting Ubuntu, you can add your XP SATA/RAID0 disk(s) ... do some research in a grub-install or grub-reinstall to make sure you install it to the PATA ...

---

### Post by amphyx on 2006-07-10
Thanks for that lightening fast response!!

Quick question ... where will it install Grub to?  will it install it to the sata raid disks or to the ide disk?  I would think it would have to be on the sata raid disk, correct?

Thanks again!
Gary

---

### Post by scxtt on 2006-07-10
i don't think it "has to" be there -- i'd keep it away from the RAID since you can select the PATA disk from the BIOS and use grub to boot XP ... but i'm not sure how you specify which disk to install grub to (you don't really get a choice on install, i assume grub-install uses options) ... you could probably also get away w/ removing (i.e. unplugging) the SATA disks so that your PATA disk is the only MBR grub sees ... cause you can edit grub.lst to point to any disk in your box based off its physical address [ hd(X,Y) ] ...

---

### Post by amphyx on 2006-07-11
Thanks for the help ... 

I went through the install, and again, everything installed properly.  Grub installed fine also, and with only the Ubuntu entries in there, they all work.

I went into the BIOS and set the IDE drive as the boot drive.  Now I would have to add the SATA Raid in to make that bootable ... when I tried that, all it did was beep like crazy --- obviously didn't modify the file properly.

So, the question is -- how do I reference the SATA RAID disks in Grub ?

Thanks again for the help!!
Gary

---

### Post by scxtt on 2006-07-11
should be something along the lines of:
```
title         Windows 95/98/NT/2000
root          (hd0,0)
makeactive
chainloader   +1
```for me, (hd0,0) is my 1st SATA disk (has breezy on it) and (hd1,0) is my 2nd SATA disk (w/ dapper on it) ... i don't know if the RAID0 will give you problems ...

---

### Post by amphyx on 2006-07-11
Thanks .. and therein lies the problem I am having ... the two SATA drives are in a RAID,  I'm assuming you can't reference a single drive in the raid, and therefore wouldn't be (hd1,0) ... but I have no idea 

Gary

---

### Post by scxtt on 2006-07-11
it shouldn't matter really, since you'd have no reason to reference the 2nd, or 3rd, etc. (mainly non-first) drive for this ... unless it's an LVM thing, maybe you can reference something like (md0,0) for the RAID disks -- can't imagine it's impossible to use grub on RAIDed SATA disks ...

---

