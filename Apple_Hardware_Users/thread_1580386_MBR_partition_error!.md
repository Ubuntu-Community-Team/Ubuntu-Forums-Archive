---
title: "MBR partition error!"
date: 2010-09-23
forum: Apple Hardware Users
---

### Post by watgrad on 2010-09-23
Hello,
I've used rEFIt and to create a dual boot system on a new MacBook Pro 7.1 following the directions in the community forum.

I can book ubuntu and mac os x fine.  However, the MBR boot table shows an error in the partition map.
See: 
Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    264650791  Mac OS X HFS+
 3      264652800    264654847  BIOS Boot Partition
 4      264654848    479217663  Basic Data
 5      479217664    488396799  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    264650791  af  Mac OS X HFS+
 3              1    264654847  ee  EFI Protective
 4      264654848    479217663  83  Linux

How can I fix this, rEFIt and gptsync are unable to repair the MBR error...
Will this cause problems (since MBR shows the ubuntu boot partition overlapping the OSX partition)?

Ideas for fixing this?

---

### Post by srs5694 on 2010-09-23
Use Linux fdisk to delete MBR partition #3 (the duplicate, and overlapping, 0xEE/EFI Protective partition).

And yes, that condition *will* cause problems. There's a bug in some utility (presumably something in rEFIt) that's creating this damaged hybrid MBR for many people. There's a post on the topic here once every few days.

---

### Post by watgrad on 2010-09-23
Thanks this worked perfectly.
There are many different options about how to solve this - and believe me I tried them all. On a fresh install of Ubuntu dual boot with OSX - this is the solution that worked.

---

