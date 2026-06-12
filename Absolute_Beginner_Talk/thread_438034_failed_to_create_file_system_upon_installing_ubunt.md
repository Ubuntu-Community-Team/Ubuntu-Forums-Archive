---
title: "failed to create file system upon installing ubuntu dapper drake"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by j_evenstar on 2007-05-09
i want to fully install ubuntu and yet the installer says 'failed to create file system' and then it continues and gets stuck somewhat at 15%. how do i solve this?

any response would be appreciated.thanks!

---

### Post by ikonia on 2007-05-09
how big is the file system your trying to create ?
what type of disk is it on ?
How long do you wait 
How long before/if it errors
Is this the exact error message

What version of ubuntu are you running ($version/$edition/$arch)

---

### Post by j_evenstar on 2007-05-09
i dunno how big the fie system is, but i chose the option erase entire disk so as to remove windows. waited about 30 minutes..

---

### Post by Ozeuss on 2007-05-09
make sure that your live CD does not have errors (run the check cd option). you can also check the .iso file md5 hash.
in order for someone to help you, you should list the specs  of your hardware. some issues are hardware-specific.
on the live cd you can see the size of your disk with "system monitor", and "gnome partition editor". the latter will also reveal the structure of your partitions.

---

### Post by j_evenstar on 2007-05-09
i've run the cd check and it found no errors. sorry but im not familiar with .iso file md5 hash.
my pc's amd athlon, 512Mb ram. accdg to gnome partition editor, i have a /dev/hda1 filesystem: ext2 size is 74.9GB used 1.18GB. the other partition is /dev/hda2 filesystem:extended, size 1.43GB. lastly there's /dev/hda5 filesystem: linux swap, size 1.43 GB.
thanks.

---

### Post by j_evenstar on 2007-05-09
thanks for all your help, i've solved the problem by using another cd!

---

