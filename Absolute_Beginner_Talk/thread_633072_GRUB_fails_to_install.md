---
title: "GRUB fails to install"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Keilious on 2007-12-06
I'm trying to install Kubuntu 7.10 64-bit (via text-install on the alternate CD), but right at the end of the installation GRUB fails to install on hd0 apparantly, causing a fatal error, I hit continue, try to install the other option "LILO" instead, which also fails.

I killed all the data from my previous windows data by deleting the previous RAID array and creating a new one at the controller.

Within the kubuntu installation, I created three equal partitions on both harddrives (root, home and swap), then hit "configure software RAID", and assigned MD for each pair.
After the first failure, I went in and deactivated the RAID array at the controller, and tried to just let the kubuntu software RAID do it alone. At the end of the install I got the same error again.

Am I missing a step? How am I to fix this?

Edit: Oh, I forgot to mention I'm trying to install in RAID0 striped.

---

### Post by Keilious on 2007-12-06
Okay, another problem...

I installed Kubuntu on just one harddrive for now until I can find out how to make it work on RAID.
I set the graphics driver to the one it detected (radeon something. Should be right, I have an ATI X1900), as well as set my monitor to the correct one. It told me to log out and restart the X server, so I did... Except it didn't load the login screen again, and doesn't even load if I reboot! It just stays on a text screen with the last line saying that boot scripts loaded OK, or something to that effect.

---

### Post by uidb4056 on 2007-12-06
If you get in text mode the promt '#', you can try to run

sudo dpkg-reconfigure xserver-xorg

then if a text window comes up you can reconfigure your settings, i recomend for first trial to select as graphics card 'vga' to see if after that are you able to get login screen after rebooting.

---

### Post by Partyboi2 on 2007-12-06
Have you tried booting in recovery mode?

---

### Post by Keilious on 2007-12-06
Alright, I managed to at least recover the system using that xserver reconfiguration command... But I still can't assign any drivers without crashing, and I cannot change my resolution from 1024x768 (well, objects get smaller when I choose a larger res, but the screen remains an equally sized box in the middle of my monitor. :S)

I'm going to try install those other ATI drivers from [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Riffer on 2007-12-06
I think installing to hd0 is wrong.  Try installing to hda instead.

On my system hda is my hard drive, I'm not sure what hd0 is, it could be your cdrom.

---

### Post by Keilious on 2007-12-06
> **Riffer said:**
> I think installing to hd0 is wrong.  Try installing to hda instead.

On my system hda is my hard drive, I'm not sure what hd0 is, it could be your cdrom.
hd0 is the right place for most systems, from what I've seen... Either way, GRUB doesn't let me choose an install location. LILO does however. I might try that, thanks. :D

Does anyone else have any suggestions for how to fix this GRUB problem?

---

### Post by Keilious on 2007-12-06
Hrum. Now I can't even get past the partitioning part! I set equal partitions on both harddrives, but when I go to configure the software RAID, and go to create an MD thing, it only gives me a list of one partition, sdb2, and automatically puts down a raid controller of only the first partitions of both disks without asking me, and I can't get rid of it!

Maybe I need to find a way to more thoroughly wipe the hard disks? How would I go about doing so?

---

### Post by Keilious on 2007-12-06
Alrighty, I made a diagnostic boot floppy and zeroed chunks of my hard drives.

Now I'm back to where I started, trying to figure out how to install this GRUB/LILO thing.

I tried writing it to hd0, md0, md/0, sda, sda1, fd0... none are working. :(

Edit: Oh, also, continuing without a boot loader it tells me to boot manually with "/vmlinux kernel" on "partition /dev/md0" with "root=/dev/md0 passed as a kernel argument".

---

### Post by Keilious on 2007-12-06
Alright... After some research, apparantly the boot can't be stored on striped RAID0.
So I'll need to create a seperate partition for /boot now, in RAID1, I assume.
Blah, my drive-zeroing floppy is apparantly broken after trying to install GRUB onto it, so I'll have to find something else to wipe the drives with again.

How much space should I partition for /boot?

EDIT: Method of putting boot in a RAID1 array fixed the problem, horray! :D

---

