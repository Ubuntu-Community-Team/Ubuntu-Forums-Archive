---
title: "Where did Ubuntu go?"
date: 2008-04-22
forum: Apple Hardware Users
---

### Post by piano08man on 2008-04-22
So, I have installed Ubuntu on my Macbook following the guidelines.  I'm trying to run Hardy Heron on a 2.0 ghz Macbook Core 2 Duo.  I created a separate partition via bootcamp and ran the installer.  I manually deleted the necessary partitions and added the ext3 partition.  I successfully completed the installer.  Then I pressed restart after everything finished.  Unfortunately the RC doesn't seem to want to restart after it finishes.  So I manually power off and can not see my Ubuntu partition.  I see it in Disk Utility on the Mac OS X side, but nothing from the boot loader or even rEFIt.  Anyone have any suggestions as to what I might be doing wrong?  Is there something I may have missed?  Any help would be greatly appreciated!

Josh

2.0 ghz MacBook Core 2 Duo Late 2006
2 gigs RAM
200 GB 7200 RPM HD

---

### Post by oskarloko on 2008-04-22
Did you installed a bootloader to choose what OS you want to use ?

If not, try to install rEFIT (I use it and works perfectly )
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

You won't see the Ubuntu partition from MacOSX, as the apple system does not recognice ext3 partitions.
I used this driver to see ext3 partitions, but a MacOSX upgrade with the driver installed broke my MacOSX installation and I had to reinstall. So I don't recommend it; and it appears to be inactive
[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

---

### Post by cyberdork33 on 2008-04-22
try running the partition tool in refit to sync the partition tables. The new installer seems to have left that part out again.

---

### Post by piano08man on 2008-04-22
Well I tried rEFIT and it seemed to install properly, but upon reboot it still went straight into the Mac OS partition.  Shouldn't I also be able to see the Ubuntu partition just by holding option during boot like a normal boot selection?  Ultimately, my question comes down to the fact that after I installed 8.04, I couldn't get back into the partition.  What can I do to fix that?  According to the MacBook Gutsy Gibbon walkthrough, it should've just showed up when holding down option after the install as a "Windows" partition.  However, I see nothing but the Mac OS X partition.  Is there possibly an issue with the downloadable images?  I've tried both the amd 64 version and the x86 version.  I haven't had any luck with either of them. 

I did run the partition tool in rEFIT but it didn't really seem to do anything.  It saw all of the partition formats but if my memory serves me correct it said that my ext3 partition was blank? or something of that nature.

Thanks!

Josh

---

### Post by oskarloko on 2008-04-22
When you installed Ubuntu,at last step before file copy and deploy on your hard drive; you pressed [Advanced] button to set your GRUB loader partition ?

Well, if you don't know what's this about the problem is that you haven't installed a bootloader onto your Ubuntu partition - so rEFIT doesn't recognice it.

If that your case, boot from CD again *( rEFIT should give you the option )* and try to enter in LiveCD mode. Then mount your Ubuntu hdd partition, chroot onto your installed system and install GRUB **into the Ubuntu partition**. Reboot and syncronize tables with rEFIT.

I think it will work.

---

### Post by cyberdork33 on 2008-04-22
before you do that, just look at the contents of your Ubuntu partition to see if there are any files. That will prove if it is empty or not.

---

### Post by violajack on 2008-04-22
> **piano08man said:**
> Well I tried rEFIT and it seemed to install properly, but upon reboot it still went straight into the Mac OS partition.  Shouldn't I also be able to see the Ubuntu partition just by holding option during boot like a normal boot selection?  Ultimately, my question comes down to the fact that after I installed 8.04, I couldn't get back into the partition.  What can I do to fix that?  According to the MacBook Gutsy Gibbon walkthrough, it should've just showed up when holding down option after the install as a "Windows" partition.  However, I see nothing but the Mac OS X partition.  Is there possibly an issue with the downloadable images?  I've tried both the amd 64 version and the x86 version.  I haven't had any luck with either of them. 

I did run the partition tool in rEFIT but it didn't really seem to do anything.  It saw all of the partition formats but if my memory serves me correct it said that my ext3 partition was blank? or something of that nature.

Thanks!

Josh

If rEFIt's not coming up on boot, it could be that it didn't install correctly.  It has been my experience that the automatic install doesn't work so it's best to include the manual commands.  

Try typing in at a terminal (in OSX):
cd /efi/refit
./enable.sh

Then, when you reboot, the rEFIt menu should come up.  The only reason to use option while booting would be if you had used bootcamp to run the installation.  If rEFIt is working it should just come up on boot, no key holding needed.

---

### Post by piano08man on 2008-04-22
Thanks for all of your suggestions.  I will definitely work on them tonight.  I didn't see anything about GRUB in the installer, so I will try again with that tonight and install rEFIT manually.  Hopefully all of that will work.  I'll update you on my progress.  Many thanks!

Josh

:guitar:

---

### Post by piano08man on 2008-04-25
So I did everything you all said; made sure that I loaded the GRUB bootloader onto the Ubuntu partition this time and everything in the installation ran smoothly.  I still cannot boot to the ubuntu partition.  I've tried installing rEFIt many times to no avail.  It will not show me a boot menu when I restart no matter if I have installed manually or automatically.  Is there another way to boot into the Ubuntu partition without rEFIt?  Below is the information the Partition Inspector from rEFIt shows me:

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    345927551  Mac OS X HFS+
 3      345927552    390720520  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    390721967  ee  EFI Protective

MBR contents:
 Boot Code: None

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+

Partition at LBA 345927552:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 3, type Basic Data


So there you have it.  Besides knowing that I installed the GRUB Bootloader and rEFIt correctly, I have found myself stuck in the same spot.  Thanks for all of your help!

Josh

:confused:

---

### Post by piano08man on 2008-04-25
duh, didn't realize that I needed to boot to rEFIt to get it working.  It's working now.  Just have to get my wireless working and I'm off.  Will be following the steps in another post.  Thanks for all of your help!

Josh

---

