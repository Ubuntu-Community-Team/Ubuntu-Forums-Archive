---
title: "I think I messed up my Master boot record"
date: 2008-11-06
forum: Apple Hardware Users
---

### Post by notphilip on 2008-11-06
Upon installing Ubuntu 8.10 on my macbook, I installed it on a new partition on my usb external hard drive. It created and installed on that new partition and didn't delete anything from my macbook's hard drive. At the end of the installation, it asked me where I wanted to boot from and by default it selected HD0. My external drive was classified on the partition table as sdb1/2 and my macbook's hard drive was classified as sda1/2. 

After installing, my macbook just shows a question mark on a folder? Did HD0 delete my boot record? How can I rectify this?

---

### Post by Frak on 2008-11-06
Press Option after the gong sound. This will bring up the Startup Disk Selector. List what disks it shows.

---

### Post by notphilip on 2008-11-06
Nevermind, I found some thread that suggested booting from a refit disc. That completely fixed it. Problem now is that the legacy os doesn't recognize my external hard drive, so I give up. Too much effort for what was supposed to be a fun small project.

---

### Post by cyberdork33 on 2008-11-07
Yes. grub-install seems to break the MBR, and in turn, breaks the Macs ability to boot from the hard drive. Just for reference, I am posting a link to the fix here:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

Also, booting Ubuntu from an external hard drive does not work (not in "legacy mode" anyway) See the FAQ extensive discussions on the subject, and well as some newer threads in the forum.

---

