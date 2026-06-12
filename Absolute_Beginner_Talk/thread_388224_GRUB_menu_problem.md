---
title: "GRUB menu problem"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Chubsky81 on 2007-03-19
I have a 3-year-old Dell with Windows XP installed on drive C (160G) and drive E is a blank 40G drive.  Everything is IDE.  I wanted to install Ubuntu 6.06 on the slave from the live CD that I obtained in the book 'Moving to Ubuntu Linux".  The install process showed /dev/hda as the C drive with Windows XP installed.  /dev/hdb was the slave that I was attempting to install Linux on and it showed the following partitions:  partition #1 of /dev/hdb as ext 3, and partition #5 of /dev/hdb as swap.  After ejecting the installation CD, I was instructed to restart the computer.  Here's were everything went to pot.  I got a 'GRUB error 21' and that's as far as I can go -- no Windows and no Linux.  I suppose the grub menu is messed up, but how to correct it without reinstalling everything?  Can anyone tell me how to get out of this little fix?  Thanks in advance and please keep it simple if you can.

---

### Post by justleen on 2007-03-19
see this thread for a possible solution: [http://ubuntuforums.org/showthread.php?t=385292](http://ubuntuforums.org/showthread.php?t=385292)

---

### Post by dstew on 2007-03-19
If you get grub error 21, you know several things. First, the grub boot stage 1 is installed correctly in the MBR of your first disk. This is good. Second, the grub stage 1 was able to find and start grub stage 2. This is good. But, grub stage 2 was unable to find the partition to use to either put up its menu, or to boot the kernel. If your Ubuntu distribution that you got from the book is similar to the regular distributions, the stage 2 boot loader will try to find and load the grub menu, which is the file /boot/grub/menu.lst. If the menu is not displayed, it could be because you did not choose to install as a dual-boot system. Another possibility is that the grub found the menu.lst file, but its display was suppressed (an option in a single-boot system), and that the error 21 came when attempting to boot the kernel.

Anyway, to start troubleshooting, it is best to try to figure out what the problem is before changing things randomly, like switching drive order in BIOS, or re-installing grub.

You can boot the Live CD, and open the terminal from the Live CD desktop, and check your system from there. To get information about your system set-up, enter fdisk -l. This will list the partitions that Linux sees. You can also mount your hard drive partitions from the Live CD boot and examine and change the menu.lst file, if that seems to be the problem.

---

### Post by gameman12 on 2007-03-19
just thought i'd put this out there. a super grub disk might be of use to you. i've never had the chance to use one :wink: but i've heard they're helpful

Link:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

