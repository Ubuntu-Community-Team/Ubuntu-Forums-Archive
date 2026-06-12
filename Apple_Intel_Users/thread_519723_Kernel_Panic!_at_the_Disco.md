---
title: "Kernel Panic! at the Disco"
date: 2007-08-07
forum: Apple Intel Users
---

### Post by radeon21 on 2007-08-07
I tried to boot camp my Macbook using the instructions here:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Upon trying to boot Ubuntu (Feisty), I got some bizarre and unfamiliar error about not being able to mount the VFS on device 0,0.  Before anyone asks, I used the lpj=8000000 boot parameter.  Also, it's 2 GHz Merom.  Thanks.

---

### Post by cyberdork33 on 2007-08-07
> **radeon21 said:**
> I tried to boot camp my Macbook using the instructions here:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Upon trying to boot Ubuntu (Feisty), I got some bizarre and unfamiliar error about not being able to mount the VFS on device 0,0.  Before anyone asks, I used the lpj=8000000 boot parameter.  Also, it's 2 GHz Merom.  Thanks.

It sounds like your root partition is not mounting. Can you post the content of /boot/grub/menu.lst (You can boot the live cd, and mount the partition to access the files.)

---

### Post by radeon21 on 2007-08-07
I've actually nuked the ubuntu partitions and plan upon installing tribe 3 this afternoon.  Do you think I needed to have installed grub somewhere besides the 'mbr'?  The walkthrough didn't mention anything about configuring grub so I assumed not and I didn't want to mess with it since I have no idea how the boot camp loader finds bootable partitions.

---

### Post by cyberdork33 on 2007-08-07
> **radeon21 said:**
> I've actually nuked the ubuntu partitions and plan upon installing tribe 3 this afternoon.  Do you think I needed to have installed grub somewhere besides the 'mbr'?  The walkthrough didn't mention anything about configuring grub so I assumed not and I didn't want to mess with it since I have no idea how the boot camp loader finds bootable partitions.

I would suggest installing rEFIt instead of relying on bootcamp.

You really shouldn't have to make any special alterations. (I think that the lpj thing has been fixed, but I might be wrong). Pop the disc in, and tell it to use the free space (if you deleted the old partitions, otherwise, use the partitioner on the install disc to delete them). You can install Grub to the MBR or the partition. It sounds like grub was configured incorrectly somehow. 

If you want a stable install I would recommend installing Feisty. Gutsy still has quite a few bugs, and these are amplified on new-to-Linux systems like Macs, and is suggested to be used for testing only by those that are familiar with Linux.

---

