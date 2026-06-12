---
title: "Trouble with RAID install"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by drive-in on 2006-08-24
I am very new to this and not up on this RAID I have or how it works. I had the computer built for video editing by someone. Now my question is....I have a RAID in my computer with 4 hard drives. I have tried installing UBUNTU newest edition but when I reboot after install, my old XP shows back up and loads after I thought the install formatted the drive. How do I install this so my old XP is gone and UBUNTU is on the hard drive? How do I do this with the RAID ARRAY?

---

### Post by zoob on 2006-08-27
I have the same problem with my XP RAID and Ubuntu.  It is like GRUB does not write to the MBR.

Kevin

---

### Post by daou on 2006-08-27
I had tons of trouble with installing Ubuntu on RAID. If I understand you correctly, you want to format your RAID array and install Ubuntu on it.

It wouldn't hurt to keep Windows dual-booting especially if you are new to Linux.

But the RAID installation isn't something to be taken lightly, and it might not work at all. But here is the howto: [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

---

### Post by daou on 2006-08-27
I just found another howto. I haven't tried it but it looks simpler than the first one I gave.

[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto")

---

### Post by zoob on 2006-08-27
Not quite.  I had 2 SATA drives.  1 250GB and 1 80GB.  The 80GB had Ubuntu on it.  I would dual boot between XP and Ubuntu with GRUB.  I added the 3rd drive, another 250GB, mirrored it and as expected lost the GRUB files.  I tried reinstalling GRUB several times with several techniques.  Finally I reinstalled Dapper again on the 80GB but GRUB still does not come up at boot.

Kevin

---

### Post by daou on 2006-08-27
> Not quite. I had 2 SATA drives. 1 250GB and 1 80GB. The 80GB had Ubuntu on it. I would dual boot between XP and Ubuntu with GRUB. I added the 3rd drive, another 250GB, mirrored it and as expected lost the GRUB files. I tried reinstalling GRUB several times with several techniques. Finally I reinstalled Dapper again on the 80GB but GRUB still does not come up at boot.

If you only want XP on the RAID-0 array, you can unplug the 80GB hdd. Then install WinXP on it. Unplug the RAID array with Windows. Then install Ubuntu on the 80GB hdd. Change your BIOS to boot from the 80GB.

Then just edit the GRUB menu.lst, adding a WinXP entry. If you dont know how to do this, have a look [here]("http://www.ubuntuforums.org/showthread.php?t=237595").

Now you can choose to boot Ubuntu or WinXP from GRUB. Plus, you can always reinstall WinXP without having to reinstall GRUB as long as you disconnect the Ubuntu hdd. Worked for me.

---

### Post by zoob on 2006-08-29
Got it!  And so simple I feel bad for posting it, but I hope this helps someone else.  Go into boot in BIOS and pick the Ubuntu drive to boot first and Viola!  Grub appears!

Thanks all,

Kevin

---

### Post by daou on 2006-08-31
> Got it! And so simple I feel bad for posting it, but I hope this helps someone else. Go into boot in BIOS and pick the Ubuntu drive to boot first and Viola! Grub appears!

I did run into that myself. Should've thought of it myself as well.

---

