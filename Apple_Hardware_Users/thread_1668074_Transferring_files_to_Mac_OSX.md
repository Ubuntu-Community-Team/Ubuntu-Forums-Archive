---
title: "Transferring files to Mac OSX"
date: 2011-01-15
forum: Apple Hardware Users
---

### Post by tpho2500 on 2011-01-15
Hi,

I have some files I want to transfer from my Ubuntu 10.04 partition to my OSX partition. I'm using GPT. The issue is that I do not have internet access on my OSX so I cannot just email them/use ftp. 

I have a 1GB flash drive but it's formatted to FAT which is not readable by OSX. I have also tried mounting my OSX partition by disabling journaling in OSX. Rebooting into Ubuntu and mounting it but OSX is still only read-only even with journaling disabled. 


I have also tried creating  FAT32 partition in Ubuntu by using GParted but because of the MSRES thing, OSX cannot mount it. I have been googling for the past 2 hours without any success. 

What can I do?

---

### Post by srs5694 on 2011-01-16
OS X is perfectly able to read and write FAT, so you should be able to use that with your USB flash drive. I've done so many times. If you're having troubles, I recommend using OS X's Disk Utility to create a fresh FAT filesystem on the flash drive and test it there. You can then reboot to Ubuntu, and if there are any problems, they'll be Linux/Ubuntu issues, which people here might be better able to handle.

I'm not sure what you mean by "the MSRES thing," unless you're referring to the Microsoft Reserved (msftres) partition type code, which was incorrectly set by some very old versions of libparted-based tools. You can easily correct this with a more recent version of the partitioner, or with my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) software, which is not libparted-based. (In gdisk, use the 't' option to change the type code to 0700, then use 'w' to save the change.)

---

### Post by sudo_0 on 2011-01-16
try this [http://ubuntuforums.org/showthread.php?t=1668467](http://ubuntuforums.org/showthread.php?t=1668467)

---

### Post by sudo_0 on 2011-01-16
:popcorn::popcorn::popcorn::D:D:D:P:P

---

### Post by sudo_0 on 2011-01-16
or for more permanent solutions try this [http://ubuntuforums.org/showthread.php?t=1668467](http://ubuntuforums.org/showthread.php?t=1668467)

---

