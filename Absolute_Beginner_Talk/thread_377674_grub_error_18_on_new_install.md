---
title: "grub error 18 on new install"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by darbytwo on 2007-03-06
I am trying to dual boot XP and Ubuntu 6.06 on a 80 gb HD but get the above error. I have tried a couple of other distro with the same result.

Is there a way to avoid this at the install stage, I have read the various answers in a google search but have to admit they didn`t mean a lot to this newbie.

Thank you

---

### Post by compiledkernel on 2007-03-06
Referencing some Grub documentation from another site 

>  This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel it self does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match......

---

### Post by dstew on 2007-03-06
Grub is trying to access a partition that cannot be reached by your BIOS. You see, Grub can only use BIOS disk reads, since the operating system has not been loaded yet. Your BIOS may not have the code to read remote sectors. If you tell Grub to use a root partition that is beyond the BIOS limit, Grub cannot read it, and stops with the error #18. In order to fix the problem, you need to change your partition scheme. If you want to use hd0,1 as your root partition, you will have to reduce the size of your hd0,0 partition, so that hd0,1 is contained withing the first 1024 cylinders. You can also change your partitions to make a small boot partition as hd0,0 and put your other partitions down on the list after the boot partition. Then, copy the grub and kernel images to the boot partition. After the operating system loads, it will be able to access your whole disk.

---

### Post by GerryB on 2007-03-06
> **dstew said:**
> Grub is trying to access a partition that cannot be reached by your BIOS. You see, Grub can only use BIOS disk reads, since the operating system has not been loaded yet. Your BIOS may not have the code to read remote sectors. If you tell Grub to use a root partition that is beyond the BIOS limit, Grub cannot read it, and stops with the error #18. In order to fix the problem, you need to change your partition scheme. If you want to use hd0,1 as your root partition, you will have to reduce the size of your hd0,0 partition, so that hd0,1 is contained withing the first 1024 cylinders. You can also change your partitions to make a small boot partition as hd0,0 and put your other partitions down on the list after the boot partition. Then, copy the grub and kernel images to the boot partition. After the operating system loads, it will be able to access your whole disk.

_ _ _ _
Thank you for lifting the fog. In practical terms, how is this done step by step? I have a live CD of ubuntu but nothing on it to correct the problem. Can I do this from "Terminal"? Can I make a bootable floppy from the live CD? Thanks again. Any info will be extremely appreciated. GerryB

---

### Post by confused57 on 2007-03-06
You might want to read this description of error 18 & other possible "fixes"
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

---

### Post by dstew on 2007-03-06
If you make your partitions correctly, the live CD will install everything in the right places. You don't have to copy the kernel and grub images yourself.

---

### Post by darbytwo on 2007-03-07
Thanks to all who have replied.

I have seen most of this during my research before I posted.

As a newbie I`m still a bit up in the air and need my hand held to solve the problem. Also I`m rather amazed that this isn`t more widely known, there must be a lot of people like me trying to dual boot on what is these days is a modest size HD.

Thank you.

---

### Post by dstew on 2007-03-07
The problem you have is not super-common these days since most BIOSes can read larger disks. Just curious, but did your system originally have a smaller disk? If you put the 80gb disk on a system that came originally with a 8gb disk, that might explain why this is happening.

Solving the problem may not be easy. If you try to make a new boot partition at the beginning of the disk, where the Windows file system resides, the partitioner will not allow it unless you wipe out your Windows OS. If you don't need a lot of space for your Windows partition, the best bet is to shrink it down as much as you can. Then put a small boot partition after the Windows partition. Then add your other partitions after that. Your boot partition would have to be entirely within the first 1024 cylinders of your disk in order to boot. The size in megabytes that you have to get your Windows partition down to depends on the architecture of your disk. What disk do you have? That is, what is the cylinder/head/sector configuration? Then we might be able to say exactly how big (or small) your partitions need to be.

---

### Post by darbytwo on 2007-03-07
Yes, I have just replaced a 40 GB HD with a 80 GB.

I have checked in the BIOS and LBA is enabled. Any ideas where I can go from here?

Thanks for you comments.

---

### Post by dstew on 2007-03-08
Clearly it is some kind of BIOS/disk compatability problem. You have LBA enabled, this is good. You can change some other BIOS settings relating to the disk. If you have a hard disk detection setting, try changing it (from user to auto). Maybe LBA has a mode setting that you can change. What is the date of your BIOS? Maybe you could update it.

---

### Post by confused57 on 2007-03-08
Sometimes setting LBA to "normal" helps...might be worth trying.

---

### Post by GerryB on 2007-03-09
> **GerryB said:**
> _ _ _ _
Thank you for lifting the fog. In practical terms, how is this done step by step? I have a live CD of ubuntu but nothing on it to correct the problem. Can I do this from "Terminal"? Can I make a bootable floppy from the live CD? Thanks again. Any info will be extremely appreciated. GerryB

You and 'Confused57' really solved my problem. I checked my BIOS after reading this:" I had the same problem. Error 18 and After GRUB. The solution is in the bios.
Put the hard disk detection on auto and not on user. It did the trick for me." I also enabled IDE hd,0. I booted from the hard drive. The live Ubuntu CD had installed everything properly. It was that simple - obviously you can say that once the solution is found. Many thanks for all those contributions and to both of you especially. Ubuntu Forum rocks! I have two good friends who are ordering the live CD already. Amazing stuff! GerryB

---

