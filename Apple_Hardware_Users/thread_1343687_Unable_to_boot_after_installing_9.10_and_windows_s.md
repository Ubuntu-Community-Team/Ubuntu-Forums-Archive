---
title: "Unable to boot after installing 9.10 and windows server 2003 on mac pro"
date: 2009-12-02
forum: Apple Hardware Users
---

### Post by dasistwas on 2009-12-02
Hi,

following setting:

I have 4 hard drives
1) /dev/sda: Mac OS X.
2) /dev/sdb: FAT32 data storage
3) /dev/sdc: Ubuntu 9.10 
4) /dev/sdd: Windows Server 2003

I installed rEFIt

I just recently installed the Windows Server 2003. Then I was not able anymore to boot into Karmic on /dev/sdc

When I boot I get the refit screen: Mac, Linux, Legacy OS, Windows but choosing Linux or Legacy OS results in a black screen on the top left corner there is just the word GRUB. I cannot do anything only force the computer tu switch off.

I did following to repair GRUB2 (LiveCD 9.10 in Terminal):

```
$ sudo mount /dev/sdc1 /mnt
$ sudo mount --bind /dev /mnt/dev
$ sudo mount --bind /proc /mnt/proc
$ sudo mount --bind /sys /mnt/sys
$ sudo chroot /mnt
$ dpkg-reconfigure grub-pc
$ sudo umount /mnt/dev
$ sudo umount /mnt/proc
$ sudo umount /mnt/sys
$ sudo umount /mnt

```
But still the same problem. Has anyone an idea how to solve this. Or is a reinstall the only option? 

Thanks for any help.
David

---

### Post by some-what-Gnu-2-networks on 2009-12-02
Did you try an alternate bootloader. Try GAG bootloader, comes w/ system-rescue-CD

---

