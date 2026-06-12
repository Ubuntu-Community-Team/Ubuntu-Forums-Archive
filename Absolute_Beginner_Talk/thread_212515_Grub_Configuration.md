---
title: "Grub Configuration"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Jax Kovak on 2006-07-10
Hi,

Thanks to some great advice from this forum I am now happily up and running inside my Ubuntu installation, but there is one thing that still eludes me.

Ubuntu is installed on the second partition of the second hard disk.
The first partition is WinXP and this is booted from the Boot.ini of the first partition on the first hard disk, which is windows 2000.

Naturally GRUB is on (hd1,1), and is bootable using the GAG boot menu, which I currently have on a floppy.

I would like to boot Ubuntu from the standard Boot.ini menu listing that currently boots the system when the floppy is not used, however, due (I think!) to the fact that GRUB is on partition 2, HD 2, if I use:
```
sudo dd if=/dev/hdf2 of=/media/floppy/linux.lnx bs=512 count=1
```
to place the subsequent file on the C: drive and boot from it I get a **GRUB Geom error** message.

I have tried to place GRUB on the first partition, however, it cannot recognise it for some reason and gives the following errors:

```
root (hd1,0)  -> Filesystem type unknown, partition type 0x7
setup (hd1,0) -> Error 17: Cannot mount selected partition
```

**Question:**
Is there some way I can get the boot sector (Or whatever it is called) that GAG is using and making work, and place it in a file on my C: drive so that I can boot Ubuntu from the standard Boot.ini menu rather than from the GAG floppy?

Many thanks

Jax

---

### Post by Jax Kovak on 2006-07-10
Hmm - I did some reading about and somewhere along the way (Cant remember where) someone was suggesting to use LILO rather than GRUB.

Would this work?

If so how would I go about installing LILO now that GRUB is already in use?

---

### Post by cotcot on 2006-07-10
Your (hd1,0) is 0x7 which means NTFS. This means that you ask grub to write to NTFS. 
Have you mounted this partition in your fstab ? (see ubuntu guide on how to do this [http://http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only]("http://http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only"))
You need to get write access. Check out this [http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support]("http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support")

---

### Post by Jax Kovak on 2006-07-10
Okay, I think can see the logic in the partition need to be mounted and writable, but surely if this had been the only HD on the machine GRUB would have been able to install to it without going through all this to mount the partition as readable?

As far as I can see GRUB would have installed on the boot record of the disk without all this mounting for reading stuff, so how come it cant do it at the moment? This is really the problem. I'm not sure I understand why GRUB cant write to the boot record as it is now.

I might be way off here: Remember that I'm very new to Linux!

---

### Post by Jax Kovak on 2006-07-11
So then. I have the instructions to show me how to install and set up LILO and I'm hoping that it will do a better job of it than GRUB under the circumstances.

Anyone think this is a bad idea and if so why?

---

### Post by Jax Kovak on 2006-07-11
Okay then. I thought that in the spirit of this community I would post this information just in case someone else has a similar problem. I hope making repeated posts like this is not breaking any rules.

Now then:

Dapper is installed on the second partition of the second hard disk and the system as a whole is booted via the boot.ini file on Windows 2000 on the FIRST hard disk.

This situation has given GRUB some very serious problems because although it installs itself onto its own partition (hdf2) it cant boot from here since the hard disk itself is not even a booting hard disk.

To acerbate this problem, using the following command:
```
sudo dd if=/dev/hdf2 of=/media/floppy/linux.lnx bs=512 count=1
```
.. to produce a file that can be used by the boot.ini on the first hard disk works but gives a "GRUB Geom Error".

The only alternative to start with was to boot with GAG using a floppy disk.

To get around this I installed LILO, allowed it to write to hdf2 (The Ubuntu installation) and then used the command line above to get a file that is now on my windows boot partition.

This works fine and I am now able to boot Ubuntu using the normal Windows boot menu as set up in the Boot.ini file

A final question (Which might end up asked as a separate one later)@

Where is the file that LILO uses for its menu, and am I able to edit it to show the items that I want?

---

