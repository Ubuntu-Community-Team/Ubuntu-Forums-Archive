---
title: "[SOLVED] the infamous error 18 in grub"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by the badger on 2007-09-26
Hi all,

I've been reading the slew of posts on error 18 and I can't get a footing in what to do next.
 i'm running ubuntu 6.06 on an athlon asus something - probably late 90s. only using 26% of my 80gig hd.** i do not have any partition**. my command line skills are nill. i can copy & paste, but i can't "poke around" in anything.

after updating something via the auto system update I started receiving error 18 on booting up. i get
```
filesystem type is ext 2fs, partition type 0x83

kernel /boot/vmlinuz - 2.6.15-29-386 root= /dev/hdb1 ro quiet splash

error 18: selected cylinder exceeds maximum supported by BIOS
```
then i'm offered up a list of about 6 different kernel versions(?): the top two (same number, but one is recovery mode) don't work. the next one down (15-28-36 recovery mode) boots up ubuntu fine.

it seems like the whole system has slowed down... i don't understand what overloading the cylinder limits means in lay-terms. should i be concerned??

help is awesome. hopefully one day i'll get to repay the favour. right now i'm lost in the glowing black screen.

---

### Post by the badger on 2007-09-26
bumpity bump...

anyone able to help?

---

### Post by kellemes on 2007-09-26
Does this thread help?
[http://ubuntuforums.org/showthread.php?p=3099335]("http://ubuntuforums.org/showthread.php?p=3099335")

---

### Post by Bothered on 2007-09-26
How big is your hard disk? It's possible that grub (or some part of grub) has been moved onto a region of your hard disk that is outside the range from which you can boot. If this is the problem, it can be solved by creating a boot partition on the front of your hard disk. I might be able to give you instructions on how to do this, but need a few more details about your system. Could you boot using the ubuntu LiveCD and post the result of the following command:

```
sudo fdisk -l
```

---

### Post by the badger on 2007-09-26
Thanks for replying -

Kellemes: thanks, i think that post you linked to gave me the command line for installing a new root partition (which seems to be what a lot of the advice is about).

Bothered: "sudo fdisk -l" gets:

```
Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9541    76638051   83  Linux
/dev/hdb2            9542        9729     1510110    5  Extended
/dev/hdb5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 500 MB, 500563968 bytes
16 heads, 32 sectors/track, 1909 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1910      488816    e  W95 FAT16 (LBA)

```

am i right in understanding that the advice to create a partition is so i'll have a new place where all the boot-up info is stored separately from the rest of the info on my hd?

---

### Post by the badger on 2007-09-27
bump!

i am still receiving an error 18 every time i try and start up ubunutu. kernel version 15-28-36 is working for me - does anyone know if i am making any sense in supposing i updated something about the kernel that doesn't work with my machine?

otherwise, does anyone know if there is any available pay-for support for ubuntu in the cheap-phone-call range?

---

### Post by Bothered on 2007-09-29
I could advise you on how to create a new boot partition without reinstalling, but it is quite a long process, and the risk of making a mistake is quite high. I think the simplest thing to do is to reinstall:

1. Use ubuntu LiveCD (or Knoppix, or similar) to make a backup of your files (e.g. to a memory stick)
2. Reinstall ubuntu, this time selecting custom partitioning at the partition options, deleting all existing partitions on your drive, and then creating three partitions on the drive as follows:

   1. Small ext3 partition (~100MB) mounted to /boot
   2. Small swap partition (1 - 2 GB)
   3. Large (rest of drive) ext3 partition mounted to /

---

### Post by the badger on 2007-10-30
Bothered -

just posting to update that (weeks later) i have successfully fixed error 18!! i was waiting for gutsy to reinstall, and after an initial mess-up, re-installed manually creating new partitions as you suggested above.

before reinstalling i [updated my BIOS]("http://ubuntuforums.org/showthread.php?t=591761") incase that would prove a later complication. also, my first re-install i forgot about that crucial re-partitioning (it'd been a few weeks since the posts here) and just re-installed: leaving me with no back-up kernel to turn to when error 18 popped up post-install. i fooled around with the [super grub disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") to no avail. nearly 24hrs later i revisited this post and realised what i'd forgotten.

functioning grub never felt so good. :biggrin:

---

