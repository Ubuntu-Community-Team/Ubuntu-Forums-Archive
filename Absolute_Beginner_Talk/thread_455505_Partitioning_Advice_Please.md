---
title: "Partitioning Advice Please"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by shellbend on 2007-05-26
Hello All,

I'm new to this forum and for the most part new to Linux.  I am eager to install Ubuntu Feisty and have done quite a bit of reading about how to partition and install, but I would really appreciate some advice about a good way to partition with my particular setup.

I have a Dell Dimension 4400 running Windows XP Home with two IDE hard disk drives and one (just purchased) External WD 500 GB USB drive for backup in case I screw everything up.

The master IDE drive is a Western Digital 37.24 GB with two partitions: 31 MB FAT (is this a hidden Dell partition, or something else?) and the remaining 37.21 GB is NTFS.

The secondary IDE drive (the jumper is set to cable select) is a Seagate 112 GB NTFS that I use for storage (my music and pictures grew too large for the first drive).  I have moved the window shell folders "My Music", "My Videos", and "My Pictures" to this drive, and it has 63.44 GB of free space.

I would like to use the secondary drive for Ubuntu because it has more space.  I have read about how to change the secondary drive to the master, install Ubuntu, and then change the menu.lst file to add windows, and this seems like a good option to me, but I do not want to completely reformat the secondary drive.

My question is this: If I make the secondary drive the master, resize the NTFS partition, install Ubuntu and edit the menu.lst file, will Windows still recognize the NTFS partition on the secondary drive as before?  Provided that the secondary drive has the same drive letter as before, Windows should locate the shell folders as before, right?  Is there a better way to do this of which I am unaware?  Are there any issues with this method of which I should be aware?

I read somewhere that the Feisty install allows Grub to be placed somewhere other than the MBR, is this true?  Would it be easier to just install Grub on the secondary drive, and then change the boot priority in the BIOS?

Thanks for your help!

---

### Post by AAM on 2007-05-26
hi, shellbend

it's actually a lot simpler than you think. First back up your beloved files, and DE-FRAG the drive. Get as much compacted as possible. - everything that moves to the left.

Using the LiveCD, click the install icon and step through the install process. When you come to the partitioning part, choose CUSTOM. The resultant screen will show "hda" and "hdb" tabs and the pre-existing 
partitions. Look for your drive #2 partition and create free space. To be comfortable you will need 5-9GB for the linux root partition (named "/", bootable and using ext3 format), a swap file of 2xRAM, and a home directory (named"/home" and using ext3 format) of the required size (?>10GB). You will be able to get your picture/sound files from the NTFS partition so don't plan to move them until such time as you wish to rid the laptop of Windows.

Then write your changes to disk. Until this point you haven't changed your HDD and so this is the crucial step.

When installed, you will find that GRUB is installed and Windows has been recognised and is an option. If you wish to change the boot order, you can edit the file with [B]sudo gedit /boot/grub/menu.lst
[/B]
I hope this helps.

---

### Post by shellbend on 2007-05-27
Thanks for the advice!  I might have been over-thinking this, but it seemed like it would be a good idea to leave the MBR on the primary drive intact so that if I should ever want to rid myself of either Windows or GNU/Linux (heaven forbid!) it would be a simpler process.

I have 63.44 GB free on the secondary drive (I have already defragmented it) and was planning to use 40 GB for Ubuntu and 1 GB for swap (I have 512 MB RAM).  Do I need to create separate partitions for the root and home directories?  If so, will the installer tell me what size I should make them?

Thanks again for the help!

---

### Post by rusty4r on 2007-05-27
I didn't make seperate partitions for root and home but every thing else I did and I have two drives like you and I used 20 gig for "/" and 1 gig for swap

---

### Post by AAM on 2007-05-27
The reason for separate partitions for / and /home is that if you want to re-install linux into that partition, both / and home will be overwritten. Having a separate /home gives you the independence to re-install without having to worry about /home. Minor point now, but may cause a minor amount of grief in future.

---

### Post by AAM on 2007-05-27
The reason for separate partitions for / and /home is that if you want to re-install linux into that partition, both / and home will be overwritten. Having a separate /home gives you the independence to re-install without having to worry about /home. Minor point now, but may cause a minor amount of grief in future.

Installer would tell you partition sizes - I suggest 9 for linux, 1 for sway and rest for home

---

### Post by shellbend on 2007-05-27
That is great advice - I didn't think about having /home on a separate partition until now...

I'm going to go ahead and give this a try now!

Thanks again for all the great advice!

---

### Post by rusty4r on 2007-05-27
I agree very good advice I have just been lucky I guess and never had to reinstall after home had much on it

---

