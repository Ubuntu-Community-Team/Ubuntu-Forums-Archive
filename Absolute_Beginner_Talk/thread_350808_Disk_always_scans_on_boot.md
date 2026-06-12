---
title: "Disk always scans on boot"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by davidY on 2007-02-01
Hi, whenever I boot my computer, it always goes into the long scan of the disk for errors - it says the reason is that there has been (a ridiculous) number of days since I last scanned the disk - usually something like 4000 days or something (not sure exactly right now). Is this to do with the fact that i dual boot windows? I notice that whenever i boot into windows it says i am in 1980....... but my linux time is always right, and so is my bios time. However, it scans the disk regardless of whether i boot into windows in between.

The interesting thing is that there are two partitions that I mount one for my /home and one for my /media/documents and only one of them needs to be checked. Both are ext3 format.

---

### Post by devils_casper on 2007-02-01
correct your windows time if possible. its marking wrong time stamp on partitions.
in case, you couldn't do that, edit /etc/fstab file and replace last digits 1 1 or watever to 0 0 of root entry.





Casper

---

### Post by davidY on 2007-02-01
> **devils_casper said:**
> correct your windows time if possible. its marking wrong time stamp on partitions

Cool, so is this time stamp fixed as long as I do not boot into windows? 

I know that the touch command sets the current timestamp on files, should (and how should) i touch all files that are on the drive? Or is there another way to fix the timestamp?

---

### Post by devils_casper on 2007-02-01
> Cool, so is this time stamp fixed as long as I do not boot into windows? 
yes.
> 
I know that the touch command sets the current timestamp on files, should (and how should) i touch all files that are on the drive? Or is there another way to fix the timestamp?
Reply With Quote

problem is, if you execute touch command and change timestamp Windows will change it again and on next Ubuntu reboot, Ubuntu will scan partitions again.
try fix to  time in Windows first and if its not possible, disable scan in Ubuntu. edit /etc/fstab file.





Casper

---

