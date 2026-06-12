---
title: "Dual boot straight to XP with 3 harddrives"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by AbsolutMayhem on 2007-08-01
Hi - I've read dozens of posts about this, but I'm a newbie and I'm really confused.
I have a Dell Dimension 40gb (XP) and a 300gb external drive [usb]. Both are NTFS. I installed Dapper on a new 300gb drive. Installation went OK but only after a couple false starts. The first 2 times it stopped with error: drive could not be formatted. 

Now when I boot up, the machine goes straight to xp.

My BIOS has an option 'Install OS mode'. It's set off. Does it need to be on? The primary and secondary slave are also both off, and CD-ROM is secondary master. I think I need to change settings, buy I'm not sure how now that there's 3 drives. During the setup I saw that the NTFS extHDD has a boot file - do I disable it? How? I'd rather not mess with jumper cables if I can help it.

Thanks.

---

### Post by sad_iq on 2007-08-01
So you installed Ubuntu on the USB drive?? Can you tell your bios to boot from usb to see what happends??? Also experiment with that setting ('Install OS mode') see if it makes any change!!!

---

### Post by AbsolutMayhem on 2007-08-02
Re: experimenting with the 'install OS' option in BIOS - When that is set to 'on' I get a warning that memory has changed to 256mb (I have 4gb installed). So I kinda panicked switched it back to off.

[COLOR="Blue"]So you installed Ubuntu on the USB drive?? Can you tell your bios to boot from usb to see what happens??? [/COLOR]
Yes. I have two 300gb-external USB drives. The first (let's call it storage) is used for storage and is NTFS. I noticed during the installation yesterday that it has a boot file on it. The second usb drive was a clean FAT drive and that's where I installed Ubuntu (let's call that drive Ubuntu). My pc's internal drive is NTFS and has XP as OS.

If I change BIOS to USB boot -which, incidentally, says usb device (not installed)- and UNPLUG the storage drive, grub loads at boot, and the linux kernel starts, then I get the following:

[COLOR="SlateGray"]mount: mounting /dev/sda1 on root failed: invalid argument
mount: mounting /root/dev on /dev/.static/dev failed : no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory  
target filesystem doesn't have sbin/init

Busybox V1.01 (Debian 1:1.01-4ubuntu3) Built in shell (ash)
Enter help for a list of built-in commands
/bin/sh: can't access tty; job control turned off
[/COLOR]
So I'm assuming that the Ubuntu installation is messed up...

BTW, if I leave the storage drive plugged in, the machine goes straight to windows, even when usb boot is enabled. I think that happens because there is a boot file on the storage disk? Maybe I need to delete or edit the boot from the storage disk?

I'm assuming I either have to unplug the storage drive or disable its boot in order to load Ubuntu. I don't have a problem with unplugging it since it's external and easy access. I'm also assuming I have to reinstall Ubuntu. There is plenty of room on the storage disk, so I guess I could install it there if it would simplify things. I was just trying to make things easier on myself by using a separate drive (hahaha - that backfired!).

When I do reinstall, should I switch the BIOS install OS button on? Will it work with only 256mb of memory? Do you think it would be easier if I just scrapped the whole third disk thing and installed Ubuntu on the storage disk?

I'd really rather lose XP altogether, but my husband will **NEVER** forgive me if he can't get to his daily fix of World of Warcraft. He's a total junkie. And he does not do well with change. So using the Cedega option would probably freak him out. Another reason I wanted to use the 3rd disk is that I didn't want to overwrite his saved game by mistake.

Any suggestions are welcome. Easiest options preferred :) .Thanks!

---

### Post by AbsolutMayhem on 2007-08-03
I solved my own prblem, sort of. I reinstalled Ubuntu to the empty drive. To boot, I have to switch boot from internal disk to USB in bios at startup, and unplug the storage drive (since it has a boot file on it, apparently for xp). Then I can boot into Ubuntu.

If anyone has any solutions about how I can delete the boot off the storage drive, so I can leave it plugged in during boot, I'd appreciate it. I'd also like to know if I can find a way to boot Ubuntu without switching the boot in bios each time. Thanks.

---

