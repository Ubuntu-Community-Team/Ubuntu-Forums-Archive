---
title: "[SOLVED] ubuntu 7.10 boots into grub, no menu.lst file"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by ScissorMeTimbers on 2008-02-07
Hi,

I've spent the past few days trying to install ubuntu 7.10, but I keep running into problems.  I have an old computer (motherboard from ~2000, Pentium 3 1.0 GHz) and a relatively new hdd, 250 GB (too big for the bios).  This resulted in me getting "error 18" when I installed ubuntu using the whole 250 gb as one partition.

So, following the instructions from threads about error 18, I reinstalled ubuntu with the following three manual partitions:
/boot, ext2, 200 mb,
swap, 1000 mb
/, ext3, [the rest]

When it finished installing, I didn't get a "Installation Complete" message asking me to reboot; the progress window just closed.  After rebooting manually, I got "error 15".  I booted from the livecd to browse my filesystem, and from I could tell, there was no "grub" directory under /boot.

I reinstalled ubuntu, specified the same partitions, but at step 7/7 (where it says ready to install), I clicked on the "Advanced..." button to get to the "Device for boot loader installation" setting.  I changed it from (hd0) to (hd0,0) and continued.  Again, no "Installation Complete" message, so I reboot manually.

Now, it boots directly into grub, ie, all I see is the grub> command line.  Using tab to auto-complete, I see a grub directory, but no menu.lst file.  I also tried playing around with the other commands, but I don't really know what I'm doing.  Entering "grub> root (hd0," and hitting tab shows me my three partitions.  Entering "find /sbin/init" finds nothing.

Can someone please help?  This is driving me nuts.

P.S. I checked the hash of the iso before burning it to cd and I also ran "Check CD for defects" which didn't report anything wrong.

---

### Post by Cypher on 2008-02-07
Any chance you can get a BIOS update to get support for your HD?

---

### Post by ScissorMeTimbers on 2008-02-07
>  Any chance you can get a BIOS update to get support for your HD?

I'll have to check on that later today, I don't have access to my home computer right now. But shouldn't the /boot partition take care of that (if I did it correctly)?

---

### Post by philinux on 2008-02-07
What's the advantage of a boot partition?

---

### Post by ScissorMeTimbers on 2008-02-07
According to some posts in this thread [http://ubuntuforums.org/showthread.php?t=11764]("http://ubuntuforums.org/showthread.php?t=11764"), it resolves error 18.

>  Re: Error 18
This is one wqay of solving it that worked for me:

When presented with the automatically chosen partitions select manual partitioning. Delete all the partitions. Add a partition. 50 MiB should be enough, but if you have lots of hdd space why not make it a 100 MiB. Select ext2 file system. And set the mount point to /boot

Now add another partition. Make it three times you RAM size and select it to be a swap partition.

Now add another partition. Make it occupy the rest of the disk. Selecte ext2 as the file system. And set the mount point to /. This will be where all the files exept for the files in /boot will reside.

Now go on with the installation.

This was done with the alternate installation cd. Don't know if it will work that same way with the Desktop cd.

/Richard

>  Re: Error 18
FYI, I have just encountered a week of this Error 16 and Error 18 business with 7.10 i386 install, and I would like to share my solution for those of you also struggling.

Briefly, here was my stall: brand new NVidia MB with Quad Core Q6600 and an internal SATA running 64-bit Vista Ultimate, then an eSATA 750GB drive to hold many things, one of which a bootable Ubuntu 7.10 i386. Problem - constant boot issues where system would not start for any one of the following reasons:

1) Missing operating system
2) Error 16
3) Error 18
4) GRUB Bootloader from within the Microsoft Bootloader (DO NOT EVER USE!!!!)

Solution:

Follow the advice of those telling you to create a small (250MB is fine) partition at the beginning of the drive containing the UBUNTU OS and then another partition for the actual OS (I used 20GB) and a third for the swap partition (I used 3GB). Then go through the install using the alternate CD, and make sure you write to the MBR (master boot record) of the UBUNTU drive.

Make sure you go into your BIOS and select the drive with the UBUNTU OS as the first HD in the boot priority. Otherwise (especially with a Vista dual-boot) you will be forced into the Microsoft Bootloader, which will FOUL UP YOUR hard drive (sda, sdb, etc) assignments in the GRUB bootloader. Best to use the /boot/grub/menu.lst as your dual/multi-boot menu. You can then edit the menu.lst file as you add more OS's to the list.

Hope this helps any of you others that happen on this thread as a result of the evil Error 18!!!!!

As I mentioned originally, having the /boot partition did seem to get me past the error 18, but now I face different problems.

---

### Post by dstew on 2008-02-07
The OP is trying to do the right thing. With old BIOSes, there is a cylinder limit to fetch files. The whole /boot partition has to be within the limit, usually about a gigabyte as I remember.

> When it finished installing, I didn't get a "Installation Complete" message asking me to reboot; the progress window just closed. After rebooting manually, I got "error 15".At this point there was clearly something wrong. I think your overall plan for the installation was correct, and there may have been an error in the installer for some reason. The error 15 means "file not found", which implies that the grub files were not placed in the /boot directory for some reason.> I booted from the livecd to browse my filesystem, and from I could tell, there was no "grub" directory under /boot.Did you mount the hard disk to the Live CD file system (or did it automount)? You have to be sure you were looking in the correct place. You have to specifically mount the boot partition, then look in the root directory of that partition for the grub directory. It would be good to make sure about this, because that will help us understand what went wrong. If you need instructions on mounting a partition to the Live CD file system, let me know.> I changed it from (hd0) to (hd0,0) and continued. Again, no "Installation Complete" message, so I reboot manually.My guess is that you had the same underlying problem as the first time, that the installer is not copying the files into the disk correctly. Putting the boot loader into (hd0,0) will not help.

Are you installing from a Live CD? If so, try the Alternate Install CD. It is a little more reliable. It uses a text-based installation program. You can get it from the Ubuntu download page, just check the box below the Start Download button.

---

### Post by ScissorMeTimbers on 2008-02-07
By the way, my BIOS version/date:

Award Software, Inc. ASUS CUSL2-C ACPI BIOS Revision 1007, 5/9/2001

Still need to find out my motherboard model though.

---

### Post by philinux on 2008-02-07
Ah right I understand about the /boot partition now.

How about splitting the drive in two with gparted then installing ubuntu on to the first and using the second as a data partition?

If you see in my sig I'm on an ol' timer too.

---

### Post by dstew on 2008-02-07
With this type of BIOS limitation the **whole** partition containing the kernel and grub files must be inside the limit. Hence, the need for a small /boot partition at the front of the drive. Once the kernel is running, it overcomes the limitation.

---

### Post by ScissorMeTimbers on 2008-02-07
> Did you mount the hard disk to the Live CD file system (or did it automount)? You have to be sure you were looking in the correct place. You have to specifically mount the boot partition, then look in the root directory of that partition for the grub directory. It would be good to make sure about this, because that will help us understand what went wrong. If you need instructions on mounting a partition to the Live CD file system, let me know.
I think I did mount them correctly.  I don't remember exactly what I did (at the office right now), but on the desktop there were "disk" and "disk-1" icons, in addition to the original two shortcuts for Examples and Install.

> Are you installing from a Live CD? If so, try the Alternate Install CD. It is a little more reliable. It uses a text-based installation program. You can get it from the Ubuntu download page, just check the box below the Start Download button.
I might try that later.

So to clarify, I won't need to update my BIOS or anything if I use manual partitions, correct?


> How about splitting the drive in two with gparted then installing ubuntu on to the first and using the second as a data partition?
Couldn't I do the same thing with the livecd installation?  e.g. create two 125 gb partitions during step 5 or 6, then just install ubuntu on one of them?  Do I need to mount the second as well? *EDIT* Nevermind, dstew answered this above. */EDIT*

---

### Post by dstew on 2008-02-07
> So to clarify, I won't need to update my BIOS or anything if I use manual partitions, correct?No, you don't need to update your BIOS. You have the right plan. We just need to work on the execution a bit.

---

### Post by ScissorMeTimbers on 2008-02-07
I just started downloading the Alternate Install CD; I will try using that later today if this doesn't get resolved by then.

Any explanations as to why I don't see the "Installation Complete" message and why I'm currently booting directly into grub? Just that the livecd installation keeps going screwy?

Thanks for all the help and feedback so far everyone. Hopefully I'll be able to get ubuntu working soon without resorting to buying a new pc (or mac).

---

### Post by ScissorMeTimbers on 2008-02-08
w00t! The alternate install CD did the trick, so now ubuntu is up and running on my computer.  However, my internet connection seems slow/flaky, but I suppose that's a different thread.  Thanks everyone!

---

