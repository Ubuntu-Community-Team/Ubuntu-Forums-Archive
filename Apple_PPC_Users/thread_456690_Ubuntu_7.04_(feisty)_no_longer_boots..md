---
title: "Ubuntu 7.04 (feisty) no longer boots."
date: 2007-05-27
forum: Apple PPC Users
---

### Post by deejay74 on 2007-05-27
hi all. i am obviously a newbie here so please forgive my ingorance.

i'm booting to this error:
"/bin/sh: can't access tty; job control turned off
(initramfs)_"

i did a search of this forum for help but the search results did not help me. i apolgize if this has been covered already. if so, kindly post the link, but first hear the rest of the story:

i'm usiing a dual 2.0 G5 with 2 drives. main drive is 150Gb and 10.4.9 is installed on it. i have a 2nd drive, which is 500Gb, and installed ubuntu 7.04 on it.

[EDIT] - i forgot to mention that when i installed Ubuntu, i had the main drive disconnected from the Logic board. i reattached it after turning the g5 off following the first boot of ubuntu. [/EDIT]

After connecting the main drive,  I rebooted to the start up manager and selected the 10.4.9 drive. when it booted, the warning message that says "you have inserted a disk that OS X does not understand" with the choices "initialize", "ignore", and "eject" on it came up . i know this is the 500Gb drive so i chose to ignore.

i rebooted again to the Ubuntu drive and after the Ubuntu load screen (the one with the slider moving back and forth) i got the error above.

one of the suggestions was to run fsck when the "boot:" prompt comes up but it doesn't recognize that command.

please help! thanks so much. :)

---

### Post by pxwpxw on 2007-05-28
Hi,

 Did the ubuntu install finish with no errors, and did it restart and run before you reconnected the macosx drive?

It might be easier to fix the problem from ubuntu if you can post  from there, but first, in macosx,
open the terminal application and get your 2 drives and partition map info using:
```

sudo pdisk -l

```
and post the result.

---

### Post by heldal on 2007-05-28
> **deejay74 said:**
> hi all. i am obviously a newbie here so please forgive my ingorance.

i'm booting to this error:
"/bin/sh: can't access tty; job control turned off
(initramfs)_"

i did a search of this forum for help but the search results did not help me. i apolgize if this has been covered already. if so, kindly post the link, but first hear the rest of the story:

i'm usiing a dual 2.0 G5 with 2 drives. main drive is 150Gb and 10.4.9 is installed on it. i have a 2nd drive, which is 500Gb, and installed ubuntu 7.04 on it.

[EDIT] - i forgot to mention that when i installed Ubuntu, i had the main drive disconnected from the Logic board. i reattached it after turning the g5 off following the first boot of ubuntu. [/EDIT]


The added information explains your problem I guess. Does the computer boot Ubuntu if you disconnect the "main drive"?

During the installation of the linux kernel, a minimal filesystem image (initramfs) is built according to how your harddrives are organised. This image is loaded along with the kernel at boot to enable loading of kernel modules to get all hardware going before normal boot resumes. During installation the content of this filesystem image would be pointing to linux being installed on the first available harddrive. When you re-installed the osx-drive, the linux-harddrive became secondary while the unchanged initramfs still refers to linux being installed on the primary-drive (now OSX). When the system tries to find the root filesystem on the harddrive it finds osx instead and fails miserably.

What you need to do is roughly:

1. Boot from the live-cd with all harddrives installed

2. Get the linux filesystems mounted for recovery (e.g. under /mnt/linux) and create the necessary device references to handle harddrives.

3. Switch to /mnt/linux as your root (chroot). 

4. Edit /boot/grub/menu.lst to reflect the fact that linux is on the secondary harddrive and not the primary.

5. Re-generate the miniroot-images (initramfs) used at boot with "update-initramfs -k all".

6. Re-write grub's boot information on the harddrive with grub-install.

7. Re-boot.

Further details can be found in the [wiki]("https://help.ubuntu.com/community/"). Look for "grub" and "recovery". If you don't feel comfortable with the recovery process you might find it easier to re-install, but keep both drives in the machine during installation this time.

---

### Post by deejay74 on 2007-05-28
@ pxwpxw - 

yes, the ubuntu did install with no errors. here is the result of the sudo pdisk -l:

Partition map (with 512 byte blocks) on '/dev/rdisk1'
 #:                type name        length   base      ( size )
 1: Apple_partition_map Apple           63 @ 1        
 2:          Apple_Free             262144 @ 64        (128.0M)
 3:           Apple_HFS Untitled 312319590 @ 262208    (148.9G)
 4:          Apple_Free                 10 @ 312581798

Device block size=512, Number of Blocks=312581808 (149.1G)
DeviceType=0x0, DeviceId=0x0


Partition map (with 512 byte blocks) on '/dev/rdisk0'
 #:                type name        length   base      ( size )
 1: Apple_partition_map Apple           63 @ 1        
 2:     Apple_Bootstrap untitled      1954 @ 64       
 3:     Apple_UNIX_SVR2 untitled 973833985 @ 2018      (464.4G)
 4:     Apple_UNIX_SVR2 swap       2937165 @ 973836003 (  1.4G)

Device block size=512, Number of Blocks=976773168 (465.8G)
DeviceType=0x0, DeviceId=0x0


> **heldal said:**
> The added information explains your problem I guess. Does the computer boot Ubuntu if you disconnect the "main drive"?

During the installation of the linux kernel, a minimal filesystem image (initramfs) is built according to how your harddrives are organised. This image is loaded along with the kernel at boot to enable loading of kernel modules to get all hardware going before normal boot resumes. During installation the content of this filesystem image would be pointing to linux being installed on the first available harddrive. When you re-installed the osx-drive, the linux-harddrive became secondary while the unchanged initramfs still refers to linux being installed on the primary-drive (now OSX). When the system tries to find the root filesystem on the harddrive it finds osx instead and fails miserably.

What you need to do is roughly:

1. Boot from the live-cd with all harddrives installed

2. Get the linux filesystems mounted for recovery (e.g. under /mnt/linux) and create the necessary device references to handle harddrives.

3. Switch to /mnt/linux as your root (chroot). 

4. Edit /boot/grub/menu.lst to reflect the fact that linux is on the secondary harddrive and not the primary.

5. Re-generate the miniroot-images (initramfs) used at boot with "update-initramfs -k all".

6. Re-write grub's boot information on the harddrive with grub-install.

7. Re-boot.

Further details can be found in the [wiki]("https://help.ubuntu.com/community/"). Look for "grub" and "recovery". If you don't feel comfortable with the recovery process you might find it easier to re-install, but keep both drives in the machine during installation this time.

yes, the computer boots to ubuntu fine with the main drive disconnected again.

i'll try what you've suggested and post the results.

thanks for your help pxwpxw and heldal.

---

### Post by deejay74 on 2007-05-28
i have another question regarding the drive that i installed ubuntu on.

if i install it with both drives connected, am i always going to get that warning message when i boot to OS 10.4.9 - the one where it says "you have inserted a disk that OS X does not understant" with the "initialize", "ignore", and "eject"?

ideally, i want to partition the 500Gb drive and install Ubuntu on one partition and have the other partition completely free of any OS so that i can use it for storage.

please let me know.

thanks again.

---

### Post by pxwpxw on 2007-05-29
Your partition table from above shows everything is in order for a default install which just uses all available space. You can do what you want by running a manual partitioning, you choose the size partitions (needs the Alternative install CD). But you have to create partitons and format them before u can use them for storage. You could probably just shrink the big partition. You decide what you need. Ubuntu only needs a maximum of about 5GB for programs, then you can add separate /home /spare whatever.

But before changing anything  you  should try a few things from the comfort of macosx to identify the present boot problem which may be simply a wrong entry in the boot configuration file known as /etc/yaboot.conf, and may happen again, so while you have macosx working, take advantage of that.

You can check all this out in macosx by mounting the Apple_Bootstrap boot partition /dev/disk0s2 and posting a copy of the same suspect yaboot.conf here. It may only need a small change to fix, which you can do in macosx with textedit as well as checking some other boot info. 

I will post precise info on that below if you want to try that, its not complicated.

I have a G5 with dual sata drives here, linux on one drive and macosx on the other, with lots of partitions, and no problem. But both drives were intially partitioned using macosx install cd or disk utility, and both have some Apple hfs partitions.
  
There is also a utility (third party) which lets macosx see and read all your linux ext3 partitions, Ext2FS_1.4d4.dmg (google it) I have it here, it works.

---

