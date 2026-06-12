---
title: "Error 22"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by oneword on 2007-09-24
Dear colleagues

My problem is quite similar to the others - except that the boot process stops immediately after the " grub" (+- 2 seconds into the process).  Currently I can access neither Ubuntu nor Vista 32.

Please provide advice to solve this error message - which also comes up when I boot from the live CD, but, at least, the CD caries on.

Alternatively , how do I UNINSTALL Ubuntu  so that I have at least my Windows. back.  No real worries.  All data on second drive; just very inconvenient. 

Oneword and clueless

---

### Post by Hospadar on 2007-09-24
I know with xp, you can use the windows boot cd, go into the recovery console, and type "fixmbr".  this will restore the windows boot loader to its original location and you can then boot off it.  then you can reformat the ubuntu partition ntfs (you may have to do that off the install cd as well as windows won't detect the ext3 partition)

---

### Post by Pumalite on 2007-09-24
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
Post:
(from Live CD after mounting your partition)
sudo fdisk -lu
cat /boot/grub/menu.lst

---

