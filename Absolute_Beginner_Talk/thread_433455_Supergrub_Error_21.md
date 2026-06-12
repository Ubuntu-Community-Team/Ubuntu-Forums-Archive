---
title: "Supergrub Error 21"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-05-05
So, I did it. I managed to bring upon myself yet another Ubuntu disaster again. :( 

[B]Please note, though, that my floppy drive socket is dead so I won't be able to use a floppy disk at all. And my motherboard doesn't support booting from usb thumbdrive.
[/B]
Here's my issue: 

1) I had 2 hard disks connected to this computer: A SATA hard disk and an IDE hard disk. Ubuntu and Win XP were installed on SATA hard disk.

2) SATA hard disk is dying so I removed it because I need to RMA it. 

3) I restored my Ubuntu image with Partimage onto my IDE drive and fixed boot with Supergrub. I then tried to boot into Ubuntu. So, I got an Error 21: Disk not found. Yes, I read up the FAQ from SuperGrub which said to reconnect the hard disk that you dismantled but that's not a solution here, is it? 

4) Then I tried many various options of restoring Grub with Supergrub from the basic "auto install grub" to even "booting ubuntu with Supergrub" and no go.

5) When I had WinXP installed, I had System recovery console installed onto another partition: that is, partition hdc1 on my IDE hard disk. So, I booted into Msdos command prompt just now after I remembered that I accidentally installed my boot files for WinXP on partition hdc1(very careless I know) and deleted boot.bak and boot.bkk :/ 

Anyways, I just had to have all these ubuntu problems sprouting up one after another. And somehow, even if I junked Ubuntu for now, I suspect that Grub might mess up my Windows XP installation too. 

Here's my ouput of "sudo fdisk -l

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hdc2            2551        7649    40957717+  83  Linux
/dev/hdc3           10200       19457    74364885    7  HPFS/NTFS
/dev/hdc4            7650       10199    20482875    5  Extended
/dev/hdc5            7650        7904     2048256   82  Linux swap / Solaris
/dev/hdc6            7905       10199    18434556   83  Linux

Partition table entries are not in disk order


Here's my output of menu.lst : 
> 
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=56e65e1a-dc07-40f9-b7e6-22f0b339dd66 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=56e65e1a-dc07-40f9-b7e6-22f0b339dd66 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.20-14-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=56e65e1a-dc07-40f9-b7e6-22f0b339dd66 ro quiet splash
initrd		/boot/initrd.img-2.6.20-14-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-14-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=56e65e1a-dc07-40f9-b7e6-22f0b339dd66 ro single
initrd		/boot/initrd.img-2.6.20-14-generic

title		Ubuntu, kernel 2.6.20-12-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=56e65e1a-dc07-40f9-b7e6-22f0b339dd66 ro quiet splash
initrd		/boot/initrd.img-2.6.20-12-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-12-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=56e65e1a-dc07-40f9-b7e6-22f0b339dd66 ro single
initrd		/boot/initrd.img-2.6.20-12-generic

title		Ubuntu, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1



---

### Post by alienexplorers on 2007-05-05
Why not just use grub from your install CD.  Load the Live CD.  Open the terminal and enter "sudo grub"
enter "find /boot/grub/stage1"
it should give you an output like (hd?,?)
enter "root (hd?,?)"
enter "setup (hd?)"
reboot and see if grub loads.

*** leave off the quotes in all statements ***

---

### Post by Lucifiel on 2007-05-05
> **alienexplorers said:**
> Why not just use grub from your install CD.  Load the Live CD.  Open the terminal and enter "sudo grub"
enter "find /boot/grub/stage1"
it should give you an output like (hd?,?)
enter "root (hd?,?)"
enter "setup (hd?)"
reboot and see if grub loads.

*** leave off the quotes in all statements ***

Ooh that's new!!! I didn't know that :D 

Anyways, trying that now and will reboot. :) 


Thank you! :)

---

### Post by Lucifiel on 2007-05-05
Oh well, that didn't work at all. :/ I still get the same error.

---

### Post by alienexplorers on 2007-05-05
Sorry that idea did not work.

Don

---

### Post by Lucifiel on 2007-05-05
> **alienexplorers said:**
> Sorry that idea did not work.

Don

Nope, it's all right. Troubleshooting is pretty much trial and error, isn't it?

---

### Post by gn2 on 2007-05-05
Do you have separate root and home partitions?

---

### Post by Lucifiel on 2007-05-05
> **gn2 said:**
> Do you have separate root and home partitions?

Separate? 

No, they're not separate. I just checked "Disk1" which contains my home and boot directory.

Edit: Hmmm, in my boot directory, I can see the kernel files and grub directory which contains stage1 and stage2.

Here's a listing of my boot directory:

abi-2.6.20-12-generic             initrd.img-2.6.20-14-generic.bak
abi-2.6.20-14-generic             initrd.img-2.6.20-15-generic
abi-2.6.20-15-generic             initrd.img-2.6.20-15-generic.bak
config-2.6.20-12-generic          memtest86+.bin
config-2.6.20-14-generic          System.map-2.6.20-12-generic
config-2.6.20-15-generic          System.map-2.6.20-14-generic
grub                              System.map-2.6.20-15-generic
initrd.img-2.6.20-12-generic      vmlinuz-2.6.20-12-generic
initrd.img-2.6.20-12-generic.bak  vmlinuz-2.6.20-14-generic
initrd.img-2.6.20-14-generic      vmlinuz-2.6.20-15-generic

And here's a listing of my grub directory:

default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5       reiserfs_stage1_5
e2fs_stage1_5  menu.lst           stage1
fat_stage1_5   menu.lst~          stage2

---

### Post by alienexplorers on 2007-05-05
In the grub directory there is a file called device.map...  Can you print out the contents of this file (cat /boot/grub/device.map) and post it here.

---

### Post by Lucifiel on 2007-05-05
Device.map

(hd0)	/dev/hdc
(hd1)	/dev/sda

Uhhh I actually opened this via gedit 'cos I couldn't get the command to work.  That is: cat /boot/grub/device.map produced output of "No such file or directory"

Edit: Thought I could install another type of bootloader but then again, that could open a fresh can of worms. :p

---

### Post by alienexplorers on 2007-05-05
If you removed the sata drive then device map should just show 

> (hd0) /dev/hdc

try removing the entry

> (hd1) /dev/sda

use sudo gedit /boot/grub/device.map

I have a feeling grub is still looking for your sata drive, so removing it from your device.map file may make it just look for hd0.

---

### Post by Lucifiel on 2007-05-05
> **alienexplorers said:**
> If you removed the sata drive then device map should just show 



try removing the entry



use sudo gedit /boot/grub/device.map

I have a feeling grub is still looking for your sata drive, so removing it from your device.map file may make it just look for hd0.

Okay done!!! 
Now, it's reboot time.

Let's see if it works. :)

---

### Post by Lucifiel on 2007-05-05
Darn!!!!

That failed, too. :/

---

### Post by alienexplorers on 2007-05-05
I wish I could be of more help.  I too had a grub error 21 some time ago when changing drives like you have.  I tried everything me and my friends could think of to get it going.  I eventually gave in and reloaded the Ubuntu package.  Luckily I had seperate /home and /data partitions so it only meant reloading the base stuff and all my preferences were saved.  I don't know if that is how yours is setup.  Again I am sorry I could not have been of more help.

---

### Post by Lucifiel on 2007-05-05
> **alienexplorers said:**
> I wish I could be of more help.  I too had a grub error 21 some time ago when changing drives like you have.  I tried everything me and my friends could think of to get it going.  I eventually gave in and reloaded the Ubuntu package.  Luckily I had seperate /home and /data partitions so it only meant reloading the base stuff and all my preferences were saved.  I don't know if that is how yours is setup.  Again I am sorry I could not have been of more help.

Hmmm...no, it's all right! :) 

I wonder if I could try installing LILO. What do you think? Reformatting could be another option, too.

---

### Post by alienexplorers on 2007-05-05
LILO might work.  I would try asking for help in the general section or maybe the installation & upgrade section before formatting and reloading the software.
Don

---

### Post by sad_iq on 2007-05-05
I think that after changing the device.map you have to reinstall grub (could be wrong thou)!!!

---

### Post by Lucifiel on 2007-05-05
> **alienexplorers said:**
> LILO might work.  I would try asking for help in the general section or maybe the installation & upgrade section before formatting and reloading the software.
Don

Yeah... hmmm... although, there's GAG too. :)

Guess I'll see what others have to say about using Lilo and gag. :p

---

### Post by alienexplorers on 2007-05-05
Try what sad_iq said about reinstalling grub like I posted in a earlier message.  Maybe that's what we are missing.  I know it's going to be some really easy fix.

---

### Post by Lucifiel on 2007-05-05
Okay yes, you're right. :)

I removed the entry for my SATA drive from device.map but didn't reinstall Grub.

Will see what happens. :) Rebooting now with Supergrub.

---

### Post by confused57 on 2007-05-05
If you have just the one drive, hdc, then your root would need to be (hd0,5)...and you might need to see if the UUID might have changed, I think the command to check UUID's is:
```
blkid
```
More info here:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

or you might change the kernel root to "root=/dev/hdc6", I'm not sure.

Added:  If none of the above works, may not hurt to do a filesystem check on the Ubuntu partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)
I'm just guessing here and the gparted live cd may be the easiest way to perform the check.

---

### Post by Lucifiel on 2007-05-05
> **confused57 said:**
> If you have just the one drive, hdc, then your root would need to be (hd0,5)...and you might need to see if the UUID might have changed, I think the command to check UUID's is:
```
blkid
```
More info here:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

or you might change the kernel root to "root=/dev/hdc6", I'm not sure.

Added:  If none of the above works, may not hurt to do a filesystem check on the Ubuntu partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)
I'm just guessing here and the gparted live cd may be the easiest way to perform the check.

Okay, do you mean the UUID in fstab?

Sorry, this is really confusing me big time. @_@

---

### Post by confused57 on 2007-05-05
I was referring to your UUID in your kernel line, but the command "blkid" should list  your UUID  for each partition...see if the results agree with the current UUID that's listed in your kernel line.  Did changing to root (hd0,5) help any?  
I think you can check the UUID of hdc6 with:
```
sudo vol_id -u /dev/hdc6
```
the link from Herman's site explains it pretty well.

Added:  You might try mounting your /dev/hdc6 and changing your root to (hd0,5):
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

then do what alienexplorers mentioned about reinstalling grub, but choose "setup (hd0)"...worth a try.  I've never dealt with grub error 21 on a single hard drive, usually it involves a 2nd hard drive and is a problem with bios being set correctly to recognize the drive.

---

### Post by Lucifiel on 2007-05-05
> **confused57 said:**
> I was referring to your UUID in your kernel line, but the command "blkid" should list  your UUID  for each partition...see if the results agree with the current UUID that's listed in your kernel line.  Did changing to root (hd0,5) help any?  
I think you can check the UUID of hdc6 with:
```
sudo vol_id -u /dev/hdc6
```
the link from Herman's site explains it pretty well.

Added:  You might try mounting your /dev/hdc6 and changing your root to (hd0,5):
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

then do what alienexplorers mentioned about reinstalling grub, but choose "setup (hd0)"...worth a try.  I've never dealt with grub error 21 on a single hard drive, usually it involves a 2nd hard drive and is a problem with bios being set correctly to recognize the drive.

All right!!! :)

Changing root from (hd1,5) to (hd0,5) in menu.lst worked!!! :)

Ubuntu now boots, although now, I've a new set of problems to deal with.

---

### Post by alienexplorers on 2007-05-05
I see that you got it working.  I knew it would be something simple.  I printed all sections of this post in case I ever get a error 21 in the future.  What other problems are you having?

---

### Post by Lucifiel on 2007-05-05
> **alienexplorers said:**
> I see that you got it working.  I knew it would be something simple.  I printed all sections of this post in case I ever get a error 21 in the future.  What other problems are you having?

Yeah, some problems are really a pain in the neck but... in the end, the solution was something that either I missed or didn't really think of. 

*sighs* Something about my ntfs volumes not being mounted 'cos they're unclean volumes.

The problem is that I no longer have WinXP installed and also, I did NOT boot into Windows XP in the last 1 week or so. Thus, I'm not sure how my ntfs volumes became dirty volumes.

---

### Post by alienexplorers on 2007-05-05
What does you fstab file have in it.  (cat /etc/fstab)

---

### Post by Lucifiel on 2007-05-05
> **alienexplorers said:**
> What does you fstab file have in it.  (cat /etc/fstab)

Here's my fstab. I edited it while I was trying to make Ubuntu boot. 

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hdc6 :
UUID=56e65e1a-dc07-40f9-b7e6-22f0b339dd66 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hdc1 :
UUID=5C4823D34823AB2A /media/hdc1 ntfs-3g defaults,locale=en_SG.UTF-8 0 1
# Entry for /dev/hdc2 :
UUID=818924b7-0379-47ba-b116-c8a4c8c736f9 /media/hdc2 ext3 defaults 0 1
# Entry for /dev/hdc3 :
UUID=2E54B5B654B5815F /media/hdc3 ntfs-3g defaults,locale=en_SG.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=70820786-09d2-497d-99e6-3cd64dea0621 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

listing of /dev/disk/by-uuid

2E54B5B654B5815F                     
818924b7-0379-47ba-b116-c8a4c8c736f9
56e65e1a-dc07-40f9-b7e6-22f0b339dd66  
96bc6efb-a635-4e2d-a8f4-9252f4adba38
5C4823D34823AB2A

---

### Post by alienexplorers on 2007-05-05
Lucifiel,

You should create a new post with your current problem.

Don

---

### Post by Lucifiel on 2007-05-05
> **alienexplorers said:**
> Lucifiel,

You should create a new post with your current problem.

Don

Oh, it's okay. I just solved my problems.

what I did was to boot into WinXP Repair Console (or Recovery Console) and run chkdsk. 

Chkdsk complained that there were some errors, then it fixed them. :)

Geez... I never knew removing WindowsXP would give me this sort of problems.

---

