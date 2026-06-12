---
title: "I/O error copying file on HDD"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Amorget on 2008-04-10
I am attempting to make a backup of a VirtualBox file I am getting this error when I drog and drop:

Error "I/O error" while copying <filename>.

This happens when I am trying to either copy from one place to another on the HDD or onto an external USB drive.  I did searches and found it happens with DVD/CD Rom drives, but not HDDs.  It fails at 6.9Gigs every time.  It's a 22.3 gb file (VirtualBox VDI of Vista).  

I have also tried sudo cp.  sudo mv worked, as I expected...

Any thoughts or fixes?

---

### Post by red_Marvin on 2008-04-10
Do you know what filesystem you have on the external drive? FAT which is quite common as default on external drives only allow file sizes smaller than 4GiB (according to wikipedia).

---

### Post by Amorget on 2008-04-10
NTFS on the external drive, however the copy doesn't even work on the same HDD/partition, which is ext3.

---

### Post by red_Marvin on 2008-04-12
I know that ntfs in linux may be problematic (due to that it was reverse engineerd), while it seems to work flawlessly for others, but that should not affect file copying between ext3 partitions of course.

I'm runnig out of plausible ideas, but you could always check the last lines of output of *dmesg* to see if it says anything interesting.

---

