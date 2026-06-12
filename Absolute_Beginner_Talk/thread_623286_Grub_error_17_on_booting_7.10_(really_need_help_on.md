---
title: "Grub error 17 on booting 7.10 (really need help on this one)"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by KTM76 on 2007-11-25
Hi.

After kicking out Windows and moving to Ubuntu I've been a happy ubuntu user for a few months. Then after a reboot I got Grub error 17 and the system wouldn't boot. My boot partition is /dev/sda1, and running sudo fdisk -l /dev/sda gives me the following list (I have 4 harddisks in total, sda, sdb, sdc and sdd in the system, but this is only showing sda):

/dev/sda1 *  1           18700   150207718+ 83 Linux
/dev/sda2     18701   19457    6080602+       5 Extended
/dev/sda5     18701   19457    6080571        82 Linux swap/solaris

This is the content of /etc/fstab:
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

When booting into the live CD, I get a lot of error for device /dev/sda and partition /dev/sda1 stating "buffer i/o error". I've also managed to enter grub on the system and issue command "find /boot/grub/stage1". This gives error message "Error 15: file not found"

I've been running testdisk on /dev/sda, and all the partitions seem to be detected correctly. I haven't received any error message when running the analysis in testdisk. 

When I try to check the filesystem by running "sudo e2fsck -p -v /dev/sda1" I get "no such file or directory while trying to open /dev/sda1. The superblock could not be read or does not describe a correct ext2 filesystem". 

I've been working on this problem for two days now and hope to receive some help, as I feel like I'm just going in circles right now...

---

### Post by Ub1476 on 2007-11-25
Maybe [Super Grub]("http://supergrub.forjamari.linex.org/") can help you.

---

### Post by annda on 2007-11-25
i second ub1476, reinstalling grub is a good idea.

also, sda1 is conspicuosly missing froms fstab - or did you post the live cd fstab?

---

### Post by njparton on 2007-11-25
Sounds like your MBR may have been damaged?

There are free MBR recovery tools out there (Google it), otherwise reinstall?

Also, make sure you set up a /home partition and then if/when you have to re-install you want loose all your personal stuff.

---

### Post by KTM76 on 2007-11-26
Hi again and thanks for the advice.

I've tried using the supergrub cd with both automatic and manual MBR repair, and neither worked. With manual repair I selected the partition /dev/sda1, which I know for a fact is my boot partition. After working for a while, I got error 24. I've also tried activating the partition, but to no avail - after a while supergrub seems to hang.

---

