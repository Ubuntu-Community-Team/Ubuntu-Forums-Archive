---
title: "ubuntu 64 hangs after install from live cd during restart"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by KroniKlepto on 2007-03-25
Hi, and hopefully thanks in advance.  

System:

Asus A8NE
Athlon 64 3500+
2gb Corsair 
Seagate 300gb SATA 3
GeForce 7600 GT

Situation:

Want to try and eventually completely switch to Ubuntu, but for now require dual boot with XP Pro.  Using Live CD, 6.10 64 ... boots fine.  I shrink my NTFS partition to 150gb, then make the ext3 partition 100+gb.  The swap is 4+gb, and a 10+gb FAT32 partition.  Place grub at 0,1.

The install process goes fine, then it needs to reboot and reminds me to remove the cd.  I click restart: I've done this 3 times now... the first time I ejected the cd before it prompted me to, then clicked enter when it said "remove the cd, close the tray, and hit ENTER."  Nothing... it just froze there.  Reset.  XP boots back up, new FAT32 partition is visible.

Second and third time through... everything installs fine, but now during the restart I wait until prompted to remove the cd.  Freeze.  Hitting ENTER until my finger hurts.  Reset.  Back into XP and here I am.

Any ideas?

---

### Post by Gilgad Drumheller on 2007-03-25
Yea, the "hit enter to finish shutdown" never worked for me on the liveCD.  Is it possible that linux has been installed sucessfully, but Windows has been named as the default OS?  I guess you'd need to look up some about the grub bootloader, see how to load different operating systems.  Maybe its a button you press right after the bios screen, or something.

Being as i havn't even been able to get ubuntu to install, thats about all the help i can give you.

---

