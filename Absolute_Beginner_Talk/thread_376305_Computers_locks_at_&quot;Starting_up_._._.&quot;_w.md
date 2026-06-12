---
title: "Computers locks at &quot;Starting up . . .&quot; when dual booting into Windows MCE"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by ormeskirk on 2007-03-04
After installing Ubuntu with Windows Media Center 2005 installed I choose Windows in Grub and it says Staring up . . . and has a cursor and does nothing else.  I have to hit the reset button on  my computer to do anything.

I read through all sorts of information about Grub and played with the menu.lst file but it never gets past that point.  

I booted off the Windows disk and "fixed" the MBR and was able to boot into windows, so I reinstalled linux again, but had the same problem.

Anybody have any ideas?

By the way, I have both OS's installed on the same drive but in different partitions.

Thanks

---

### Post by chuckyp on 2007-03-05
Something is getting messed up with the menu.1st file.  Are you able to boot in to linux?  If so can you post your /boot/grub/menu.1st file so we can take a look at it.

If you can't boot in to linux you can also try one of the ext3 file viewers availible for windows to view your linux partition and post the file that way.

---

