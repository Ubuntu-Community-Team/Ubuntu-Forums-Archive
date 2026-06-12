---
title: "Unable to mount anything to /dev/sda"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by gilbre on 2008-04-08
I have an A-Data 16GB flash drive (model PD16) that I tried to install a bootable copy of Ubuntu 7.10 on.  However, something went very wrong and now Ubuntu will not recognize this particular drive, however Win XP will.  Additionally, Ubuntu will recognize all of my other usb flash drives (as sdb1, sdc1, etc.).  The drive that won't mount always tries to mount to sda.  I have tried several of the help files on this forum and had no luck.

The Flash drive was recognized initially..
I used pendrivelinux.com as my install guide for this.
The point where my install failed during install:
# Type umount /dev/sdx1 to ensure the 1st partition is unmounted
# Type mkfs.vfat -F 16 -n ubuntu710 /dev/sdx1 to format the first partition
# Type umount /dev/sdx2 just to ensure the 2nd partition is unmounted
# Type mkfs.ext2 -b 4096 -L casper-rw /dev/sdx2 to format the second partition
# Remove and Re-insert your flash drive
# Back at the terminal, type apt-get update
# Type apt-get install syslinux mtools
# Type syslinux -sf /dev/sdx1
# Type cd /cdrom
# **[COLOR="Red"]Type cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz /media/ubuntu710/[/COLOR]**

So the Ubuntu Live CD would no longer recognize my drive.... and after the files didn't copy I figured I should go back over to windows and use Disk Management to remove the partitions and re-format.  Then I booted to Gutsy and it wouldnt recognize it there either.  I have went through several things to figure this out...  no luck.

I do know that in my /dev/ directory when I plug this drive in I get 3 or 4 usbdev*.* folders that seem to get created.  This does not happen with my other USB flash drives.

when I run 'lsusb' it is recognized, but when I run 'fdisk -l' it is not.  

As a side note I have reformatted using the A-Data partition tool.  It seems to me that this could be a file related problem.  Bad placement, bad couple lines, etc....??????

If anyone has ANY suggestions I will give them a try!  Thanks in advance for your help.  If you need any information let me know.

---

### Post by jameswillmer on 2008-04-09
i have tried pendrivelinux previousl as well - no dice my particular USB stick

let us know if you do succeed

did you try to reformat in Winxp yet?

---

### Post by rustutzman on 2008-04-09
Did it's last use happen to be in a Windows machine? Been my experience that if you didn't use the "Safe to remove hardware" thing. Ubuntu wouldn't mount it. I went back in to Windows and did the "remove  hardware" then tried it again in Ubuntu and it mounted.

Check out "Storage Device Manager" 
[http://pysdm.sourceforge.net/#downloads](http://pysdm.sourceforge.net/#downloads)
It may help. I've used it with good results.

Russ

---

### Post by gilbre on 2008-04-09
I have tried reformatting it in XP and using the AData reformat tool.  Started back up in Gutsy and had no luck.

I tried out gparted as well and it doesn't recognize my drive..  It seems like a file got messed up somewhere on my install!

Will definitely try PySDM and let you know.

---

### Post by gilbre on 2008-04-09
I attached the results from running dmesg and lsusb.  The Prolific Technology, Inc at BUS1, DEVICE3 from the lsusb command is my usb drive that won't mount.

---

### Post by Presbuteros on 2008-06-30
I have the exact same model jumpdrive as you, the A-Data PD16. I have tried for hours to mount this thing and still nothing... I even tried erasing the MBR completely to RAW to see if that would work and still nothing... So I will stay tuned for answers. I am running 8.04 though...

---

