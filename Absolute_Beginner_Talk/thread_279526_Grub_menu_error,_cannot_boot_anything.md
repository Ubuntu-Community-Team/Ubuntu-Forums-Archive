---
title: "Grub menu error, cannot boot anything"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by peterj on 2006-10-18
Hi, I really appreciate any help on this as ive literally tried everything. I am a new user and to be honest, I'm out of my depth, on the bright side, Im ready to scrap windows for good! I will try and stay brief by listing in point form!!

- spilt coffee on laptop, cd rom is a write off, no probs until now though... no money to buy external!
-resize my ubuntu partition, now ubuntu won't load, error is to do with file systems.. (below)
-delete ubuntu partition completely for a re-install
-error loading grub menu, error 22--now no windows, no ubuntu, no cd rom!
-install fresh ubuntu on an external through other box, plug in and boot from external, gets to waiting for root file system, then takes ( mins and then same error as before, (below)
I tried editing the grub menu and puttting in windows; tried a few combos and nada, 
-an boot this version on another comp and edit if it will help.
-my terminal work is, er, basic!
-I think its the ntfs thats the problem, Ive searched the error message a milklion times and no solutions.

alert! /dev/sdb1 does not exist. dropping to shell
/bin/sh cant access tty; job control turned off.

Again, really appreciat any help at all. I have no access to a usb cd-rom.
Thanks
Peter

---

### Post by caravel on 2006-10-18
GRUB was installed in the master boot record of your windows partition, by nuking the partition containing Ubuntu you've broken the bootloader, rendering the system unbootable.

Personally I would clean off Ubuntu and, if possible boot from your XP CDROM and restore the master boot record (recovery console, then "fixboot"), then start again afresh.

---

### Post by peterj on 2006-10-18
Thanks for the reply, problem is the cd rom is caffienated!

---

### Post by peterj on 2006-10-18
Any ideas anyone? any programmes i could boot of an external hard drive that could help me fix it? please?!

---

### Post by anaconda on 2006-10-18
You could also boot with a (win98 rescue) floppy, and then type:
fdisk /mbr
it would restore your mbr back to what it is supposed to be.. so that you could boot to windows. (mbr hasn't changed in the past 15 years, so you could use any old bootable floppy which has fdisk..))
Or install lilo, which is a bootloader, that fits completely to mbr

Or install a new linux from usb-stick.. eg. DamnSmallLinux, or ubuntu.. There is instructions somewhere in the wiki..

---

### Post by caravel on 2006-10-18
Do you have a floppy drive in there?  You could boot from a DOS/Win9x boot disk and do: fdisk /mbr that will also fix the bootloader.  You could also transfer the system to the external HDD and use that as, effectively, a DOS boot disk.

You need to be careful when resizing partitions, when installing.  It's rather dodgy.  It's a good idea to defragment the windows partition before hand and be sure of how much space you have to play with.

-Edit: I didn't see anacondas post before i posted mine.  The USB flash drive is a good idea also. ;)

---

### Post by Herman on 2006-10-18
Super Grub Disk for USB devices,[* Click Here*]("http://adrian15.raulete.net/grub/tiki-list_file_gallery.php?galleryId=5")

This is not the latest version of Super Grub Disk as available for CDs, but it should boot your operating systems for you.

Regards, Herman :D

---

### Post by peterj on 2006-10-20
phew! Problem solved, thanks for the advice guys. I forked out for a cd-rom, 80 euro well spent... especially when I bought it back to the shop an hour later and got my money back.. mwa ha ha

---

