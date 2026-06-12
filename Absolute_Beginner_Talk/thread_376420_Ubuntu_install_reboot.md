---
title: "Ubuntu install reboot"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by LieToPurify3 on 2007-03-04
after i install ubuntu from the live cd, it is supposed to show a status bar shutting down and then one rebooting.  the shutdown bar that moves backwards, gets the last bar and a half, and never moves past that! i cant start up without the cd in the drive because it never actually finished loading the OS onto my hard drive. any ideas? i'm an absolute beginner. this is my first time using/installing any linux or ubuntu system.

---

### Post by chuckyp on 2007-03-05
Well actually it should have finished the install maybe just not finished killing off all of the processes running in the background when the bar is moving backwards.  Perhaps check the media make sure the CD is good.  Also you may wan to try hitting ctrl+alt+f1 when it is hanging to see if there is any output on vt 1.

---

### Post by LieToPurify3 on 2007-03-05
well i burned 2 cds for ubuntu, and ahve the same problem with both. so now i did the same with xubuntu, and now when it says to click restart, the screen gets all weird and it just hangs there. i pressed ctrl alt f1, but i cant read the text since the screen is all messed up. i'm downloading the alternate install cd for ubuntu right now. i'll see if that works. i think my hard drive might be corrupted. so if this doesn't work, im gonna go buy a cheap HD and try that.

---

### Post by LieToPurify3 on 2007-03-05
i'm trying to use the alternate insall cd for ubuntu right now. i'll let you know if it works

---

### Post by LieToPurify3 on 2007-03-05
i installed the alternate cd, but after reboot, it sayd "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER".  It says the same thing whenever i tried restarting when the reboot failed wiht the live cds for ubuntu and xubuntu. whats wrong!?

---

### Post by vinchi007 on 2007-03-17
CHeck your BIOS and make sure CDROM is in first boot sequence, then HDD (hard disk). Then try to restart again from live.
Once live booted up, check your partitions with GParted and see if you have any partitions on your HDD.
If you do see, then something went wrong during installation, and need to reinstall GRUB, or better whole linux.

---

### Post by jerroddevon on 2007-04-26
> **vinchi007 said:**
> CHeck your BIOS and make sure CDROM is in first boot sequence, then HDD (hard disk). Then try to restart again from live.
Once live booted up, check your partitions with GParted and see if you have any partitions on your HDD.
If you do see, then something went wrong during installation, and need to reinstall GRUB, or better whole linux.
Quick question. How can I check my BIOS if all i get is a black screen that says "disk boot failure insert system disk and press enter". What do I have to enter to get to the Bios screen?

---

