---
title: "Upgrade hard drive on triple-boot MacBook"
date: 2009-12-31
forum: Apple Hardware Users
---

### Post by mdgill on 2009-12-31
I have a new 500 GB hard drive to replace my MacBook 4,1 120 MB hard drive.  I used dd to clone the 120MB to the 500MB.  I was surprised it worked.  Then, I extended the last partition, the Windows partition, using the Microsoft partition editor.  Once again, I was surprised it worked.

Unfortunately, none of the other OS's (Mac OS and Ubuntu) now do much more than recognize the extended partition as the same size as the old partition.  NTFS-3G balks to normal, read-only NTFS in Mac OS, and the data in the extended region is unreadable.  The disk won't mount in Ubuntu.

rEFIt also seems to be having trouble.  I ran the partition mapper, and it re-mapped it smaller instead of larger.  Now, I have to boot into Grub to get to Windows, and now it won't reboot.  I get the Windows progress bar, but I never get to the blue circle with the Windows symbol in it.  Safe-boot doesn't boot up all the way either.

Any ideas?

I lost my Mac OS installation disks, btw, and would rather not reinstall anyway.

---

