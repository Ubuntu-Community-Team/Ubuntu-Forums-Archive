---
title: "Problem with Ubuntu DapperFlight... Please help"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by nubuntux on 2006-03-04
Dear all:

everything was fine during my dapperflight installation. i partition my 60G HDD with the ff. order:

hda1      NTFS Windows XP
hda2      FAT32 storage
hda5      FAT32 stoage
hda6      FAT32 media
hda7      EXT3 Ubuntu dapperflight
swap     512 linux swap

after installing GRUB, then reboot... i've encountered this error message:

[B]Booting 'Ubuntu, kernel 2.6.15-15-386'
root (hda0,6)
.
.
.
save default
boot
Uncompressing Linux... OK, booting the kernel.
ALERT! /dev/hde7 does not exist. Dropping to a shell!

[/B]What's wrong with my filesystem, since i choose hda7 for my ubuntu installation but after that, dapper change hda7 to hde7? 

How do i fixed this?

---

### Post by cotcot on 2006-03-04
I see that your dapper /boot is not on a primary partition. Maybe that is the problem.

---

### Post by Madpilot on 2006-03-04
There's a seperate forum for the Dapper beta testers - trying there will probably get you far more information than here.

Keep in mind that Dapper isn't stable yet, it's still in heavy development. If you want a stable Ubuntu, get 5.10 (Breezy Badger)...

---

