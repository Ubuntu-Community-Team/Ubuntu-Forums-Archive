---
title: "Bit of a problem with folder and question mark"
date: 2009-11-10
forum: Apple Hardware Users
---

### Post by lopol on 2009-11-10
So I tried installing the latest Ubuntu on an external drive, which has caused some problems and now basically my mac wont boot at all. I have reinstalled os x from the original disks but still just get the folder with a question mark. Reset pram, and selected the disk in disk utility (via disk) but still no joy.
 
Oh and I can't boot into ubuntu either, except through the cd.
 
I have read topics similar but they got a bit complicated. Surely whatever it has effected could only be on the hard disk, so reinstalling should have fixed it?
 
I will install it the normal way when this is sorted and have it bootcamp, just didn't have much space. 
 
Any one know anything I could do?

---

### Post by linuxopjemac on 2009-11-10
from the MacOS installer CD boot from it, then go to Disk Utilities and partition your disk in two parts. One HFS plus partition for OSX and one other for Linux, doesn't really matter which type, you will format it anyway to ext4. Install OSX on the HFS plus partition and install rEFIt. Then install Ubuntu from the Ubuntu CD and then sync the partitions from the rEFIt menu then you should be able to boot into Linux. If all goes well you will have 
/dev/sda1 (EFI)
/dev/sda2 (OSX)
/dev/sda3 (ext4 - Linux)

---

### Post by lopol on 2009-11-10
ok i followed your info, but since i installed refit, should I install a boot loader? *confused*
 
Thanks.

---

### Post by linuxopjemac on 2009-11-11
the boot loader is installed when you do the Ubuntu installation

---

### Post by oX Milady Xo on 2009-11-29
I have a very similar problem, the difference being I do not have a Mac OS recovery disc. Is there another way? 
 
~I did find: 
 
*Name: vmlinuz*
*Type: link (broken) (inode/symlink)*
*LinkTarget: boot/vmlinuz*
 
This file is in my Mac OS as well as my ubuntu OS. Is it overriding my Leopard boot file? Considering the file is in grub which Leopard cannot read...
 
~I've tried exchanging hard drives and using the one with Leopard as an external, still could not be found. 
 
~I can see all my pictures, videos, and documents from running ubuntu on the disc, just can not access them.
 
~I tried actually installing ubuntu on the same hard drive this time, and the question mark with the folder still pops up.
 
**My story**:
 
"I was installing ubuntu on an external hard drive connected to my mac (OS Leopard) when the computer prompted me to restart to finish the install. I did, and the grayish screen pops up after a minute with the question mark folder blinking. I have tried safe mode, option, resetting the PRAM, and a hardware test, and nothing happens other than the blinking question mark folder. 
 
Now, when I insert my ubuntu disc into the drive, the macbook will read it so that I may run the operating system. Through ubuntu, I can view Macintosh Operating System which still contains all of my folders and documents. I cannot copy them to an external source or access them, just merely know that they are there.
 
I do not have a Mac Recovery Disk and am confused on what to do in order to get Leopard to load so that, at the very least, I can retain my files and documents before starting over again."
 
Thanks for any information or advice!!!
 
UPDATE: Solution Found!! 
 
Playing and fiddling does in fact work! 
 
Solution:
1) Remove internal hard drive and connect to usb port
2) plug usb port to other Mac OS system
3) Format hard drive without erasing files (repartition to same amount of memory being used before)
4) Mac will boot slower, but problem fixed!

---

