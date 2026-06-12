---
title: "deleting a partition, and resizing ubuntu's partition"
date: 2009-01-15
forum: Apple Hardware Users
---

### Post by skullmunky on 2009-01-15
Just wanted to check that this is ok & correct before I do it:

I have a MacBook Pro (1,1) set up for triple-boot, with partitions for OSX, Windows, and Ubuntu in that order (in addition to the EFI partition of course).  I never use Windows (actually, it never worked at all :) and I'm running out of space on the Ubuntu partition, so I'd like to delete that middle partition and expand the last one.  My plan is to do this:

1. boot into live cd
2. run gparted
3. delete the windows partition, and resize the ubuntu one
4. reboot
5. in the EFI shell, sync the partitions

Question 1 - is it ok to resize a partition by expanding towards the beginning of the disk, instead of towards the end? (making partition 4 swallow partition 3)

Question 2 - any steps I'm leaving out or risky places this could go horribly awry?  

thanks!

---

### Post by cyberdork33 on 2009-01-15
That will:
a) probably mess up the bootloader (grub) and it will have to be reinstalled...

b)change the partition order and thus the menu.lst file will need to be updated to relect the change.

---

### Post by skullmunky on 2009-01-16
hmm, nuts.  thanks.  think i'll just make it into a shared data FAT32 partition instead.

---

