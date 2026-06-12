---
title: "[SOLVED] How-to Recompile a kernel without overwriting data"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-12-18
I have a boot disk that got hurt, when I unknowingly plugges a windows 98 disk into the slave posiiton on the cable.

Since that date, I cannot boot the drive. That is boot it to a state of workingness.

I have been using SuperGrub for several weeks now and have the Grub "splash" screen up, i.e., I see the various 2.6.14.x "selections" available.

All but one of the selections returns a Grub Error 15. And from 

Gentoo Grub Error Collection ([http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap1](http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap1))
I see the exact same problem:
[B]
4. Grub Error 15

Situation

This error can occur in two different stages of the GRUB configuration, either during the initial configuration (installing GRUB in the master boot record) or after booting the system and attempting to launch Linux (or any other entry).

Code Listing 4.1: Grub Output - Initial Configuration

grub> root (hd0,0)
 Filesystem type is xfs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

Code Listing 4.2: Grub Output - Booting an Entry

Booting 'gentoo Linux'

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel (hd0,0)/boot/kernel-2.4.20 root=/dev/hda3 vga=792

Error 15: File not found
Press any key to continue...

Solution - Initial Configuration

This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

Frequently, the error notes a missing kernel image file. Make sure that the file it is referring to exists on your boot partition.

To find out the exact name of your kernel, boot from the installation cd, mount your root and (if applicable) boot partition. Next, chroot into your Gentoo system and do a listing of the available files to see what kernel images you have available:

Code Listing 4.3: Verifying kernel image existence

# cd /boot
# ls

This will list all the kernels that you've got on your boot partition. If your kernel is missing make sure that you compiled a kernel (using genkernel or manually):

Code Listing 4.4: Recompile the kernel

# cd /usr/src/linux/
# make menuconfig
# make

And that you copied it to your boot partition:

Code Listing 4.5: Copying the kernel

# cp /usr/src/linux/arch/i386/boot/bzImage /boot

Verify that the name of the kernel is exactly the same as the one mentioned in your grub.conf file. Also make sure that the kernel line in your grub.conf file is referring to that partition (either explicitly or implicitly).

Another reported mistake is to have the BIOS ignore the disk on which the kernel or grub stages reside. Also, the partition on which grub stores its stages should not use a software RAID-5 (or other striping technology) configuration.

Solution - Booting an Entry

First, verify that the root and setup lines you have used are correct.

If you are certain they are valid, then you might be using a flawed GRUB version (0.93.20031222). Upgrade your Portage tree or mask this version of grub:

Code Listing 4.6: Masking Grub

(Execute this from within the chrooted environment)
# echo "=sys-boot/grub-0.93.20031222" >> /etc/portage/package.mask
# emerge grub -p

You could also try to use the grub-install script as is recommended by the GRUB authors:

Code Listing 4.7: Using grub-install

(The --root-directory is needed if you are using a separate boot
partition, 
 otherwise you should leave it out)
# grub-install --root-directory=/boot /dev/hda

When all this fails, your boot partition may be corrupt. Check the partition for errors:

Code Listing 4.8: Checking a partition for errors

(Make sure the boot partition, /dev/hda1 in this case, is unmounted)
# fsck -y /dev/hda1[/B]

If I have to recompile the kernel, will I lose the /home's files? Also, can someone tell me if SuperGrub can "operate" on a disk in a usb cradle?

---

### Post by Thelasko on 2007-12-18
First of all, stop reading stuff about Gentoo.  They recompile everything and it's completely unnecessary.

Stick with this site and you will get the information that you need.

Fortunately, some other people have made the same mistake you have and [posted the solution here.]("http://ubuntuforums.org/showthread.php?t=210820")  

This is just the first page I found by searching for "repair grub."  You might want to try several more.

If all else fails you can save everything you have in your /home directory, reinstall Ubuntu and put your /home back.  But I think it can be saved by reconfiguring/reinstalling grub.

---

### Post by Mark_in_Hollywood on 2007-12-18
> **Thelasko said:**
> First of all, stop reading stuff about Gentoo.  They recompile everything and it's completely unnecessary.

Stick with this site and you will get the information that you need.

Fortunately, some other people have made the same mistake you have and [posted the solution here.]("http://ubuntuforums.org/showthread.php?t=210820")  

This is just the first page I found by searching for "repair grub."  You might want to try several more.

If all else fails you can save everything you have in your /home directory, reinstall Ubuntu and put your /home back.  But I think it can be saved by reconfiguring/reinstalling grub.

**I have been reading and posting at this forum about this for over 2 weeks about this problem. AND my questions remains: If I follow the instructions on the page you show, linked above, will I overwrite my /home files?**

As I tried to save this and repost, I received a message that the post was too short. Go Figure!

---

### Post by psusi on 2007-12-18
Recompiling your kernel will do nothing to fix grub, and commands used in that message like emerge do not exist on Ubuntu.

You mentioned that you plugged in a slave disk drive.  I assume it is still connected and if you disconnect it, the system works?  Could you describe your disk configuration?  Do you have more than these two hard disks installed?

Instead of pressing enter to choose the option to boot linux, press e to edit the command.  You should see a part that looks like:

```
root (hd0,0)
```

Change the hd0 part to hd1 and press b to boot.  You might also try 2 if 1 does not work.

---

### Post by Thelasko on 2007-12-18
If you **only repair Grub** it should not touch your /home directory.  All we are doing is reinstalling one program.  That being said, it's always a good idea to backup your /home directory in case the worst happens.

If you have sensitive information on your hard disk and can't get it off (there are ways to get it off with the live disk) then **don't reinstall Ubuntu!**

---

### Post by Mark_in_Hollywood on 2007-12-18
It took quite a bit of doing, from the 40 gig that has the grub problem; the files in /home were transferred to a 20 gig, that was pri/slave but was set in bios to boot. Once those files were moved, I put the 20 gig in a usb cradle and moved them all again.

SUCCESS!

Thanks, Community

Merry Christmas

---

