---
title: "Ubuntu PPC no longer boots, only OSX"
date: 2009-08-23
forum: Apple Hardware Users
---

### Post by markosjal on 2009-08-23
I have an ibook that I installed Ubuntu 9.04 on for a friend. It worked fine for several reboots, however now it only boots to Mac OS X (10.4) . I no longer even see yaboot, just boots straight to OSX. 

The disk is as follows:

75 Gig
 MAC OSX 25 Gig
 "files"*
 Ubuntu 9.04

* Most recently this "files" partition was changed from an OSX Partition to a FAT32 partition, but as far as I know it has nothing to do with yaboot, nor ubuntu. The system booted to ubuntu at least twice after making this change.

I believe the problem started after trying to mount the FAT32 partition in OSX , but as far as do anything to the Ubuntu partition, I did nothing that I am aware of. Does the Mac OS Disk Utility make changes on the sly? In fact since I have no password to the Mac OX system , I was not even able to mount the disk. 

Anyone else ran into anything like this?

Thanks,

Mark



UPDATE

I just booted to the Live CD and changed the boot partition to the EXT3 partition, which I assume is where it should be , but upon a reboot, I got Mac OSX again

Mark



UPDATE

Looks like there is a 1 Meg boot partition that has yaboot. I set this to the active boot partition and still no go. How do I fix the boot partition?

---

### Post by ditsch on 2009-08-24
You have to restore your yaboot bootloader with ```
sudo ybin
```. To get into the system to execute that command, you can use booting with the Option key pressed, which lets you then choose the boot volume.

Alternatively, you can use the Live CD to chroot into your system.

---

