---
title: "[SOLVED] GRUB Question"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by SilverDragon on 2007-01-28
Okay I'm trying to fix GRUB(not hide it) so it allows me to boot right up into Windows, because I just don't have time for Linux at the moment and it also bothers other people who use this computer.

Using these links: [http://users.bigpond.net.au/hermanzone/p15.htm#If_you_want_to_restore_the_Windows_boot_sector](http://users.bigpond.net.au/hermanzone/p15.htm#If_you_want_to_restore_the_Windows_boot_sector)

and this one

[http://www.kellys-korner-xp.com/win_xp_rec.htm](http://www.kellys-korner-xp.com/win_xp_rec.htm)

I go into the Recovery console, but I'm not really sure which Windows installation I'm supposed to log into too. I tried 1 and it worked, but I have 2 hard drives, so I was thinking I should have typed 0, because the MBR would be on the master drive, right? I got this that idea about the two hard drives from this thread: 
[http://www.ubuntuforums.org/showthread.php?t=329250](http://www.ubuntuforums.org/showthread.php?t=329250)

Either way I used the command fixboot and it seemed to work, but when I typed the command fixmbr, this shows up:

**Caution**

This computer appears to have a non-standard or invalid master boot record.

FIXMBR may damage your partition tables if you proceed.

This could cause all the partitions on the current hard disk to become inaccessible.

If you are not having problems accessing your drive, do not continue.

Are you sure you want to write a new MRB?


I'm thinking it's invalid cuz GRUB wrote over it, but I'm not sure, so I thought I'd ask and because other people have made it so they couldn't boot into Windows at all. I found a link  showing you how to save your MBR on Linux, but not on Windows, but if I just write a new MBR, I think it'll be fine.

---

### Post by geezerone on 2007-01-28
You don't have to 'fixmbr' which will overwrite your MBR on your primary boot partition and thus wipe Grub off. Instead, why not edit your 'menu.lst' file (/boot/grub/menu.lst)  and make the 'timeout = 1' with other unuseful options hashed out? 

This is a much simpler way IMHO and allows you to boot into Ubuntu when you require.

The Fixmbr will overwrite the boot partition and I have used it once successfully but backup important data just in case.

---

### Post by SilverDragon on 2007-01-28
I would try that if I could get into Linux. In this thread:

[http://www.ubuntuforums.org/showthread.php?t=345076&page=2](http://www.ubuntuforums.org/showthread.php?t=345076&page=2)

It looks like I'm having problems with my hardware, and maybe it has something to do with me having to install Ubuntu using the noapic boot parameter, but I'll probably end up reinstalling Ubuntu on my slave drive.

Either way how would I back up my MBR on Windows?

---

### Post by LxP on 2007-01-28
Log into Windows and type **fdisk /mbr**.  Personally I would ignore any warning that might show up (although I've never experienced that).

If that doesn't work from within Windows, you might have to do it through the Recovery Console.

---

### Post by SilverDragon on 2007-01-28
I ignored the warning and it worked :-)

Thanks to the people who helped. :-)

---

