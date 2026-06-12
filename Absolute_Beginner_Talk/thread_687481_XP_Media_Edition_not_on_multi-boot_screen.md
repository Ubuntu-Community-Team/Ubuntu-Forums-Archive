---
title: "XP Media Edition not on multi-boot screen"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by J Caffrey on 2008-02-04
I finally got my ubuntu 7.10 installed correctly having managed the partitions properly.In the long and laborious process I crashed my XP.I reinstalled it from the backup discs into the second partition but it doesn't show up in the multiboot menu.I have Partition Commander which shows the complete drive as:partition(0)recovery,partition(1)WinXP)(free space) partition(2)ext3 Linux and then the swap file.How do I enter XP asI have young Children who can only use XP

---

### Post by bumanie on 2008-02-04
If xp is showing 'free space', it would seem that the recovery disc has not reinstalled xp.  May be you'll have to use the recovery partition, by pushing whatever F key it tells you on boot up. This will wipe everything else you have on the drive and reset the computer back to how it was when new. Alternatively you could get a copy of test disk (live cd data recovery program) and see if you can recover xp via that tool.

---

### Post by dstew on 2008-02-04
You should be able to boot the Windows system from the Windows CD recovery console. If you can, then you know that it is installed correctly. If it is installed correctly, you can add a Windows menu item to the grub boot menu by editing grub's configuration file, which is /boot/grub/menu.lst in your Ubuntu system.

If you can't boot Windows from the recovery console, then go to Ubuntu, open a terminal and enter the command```
sudo fdisk -l
```This will print a list of your partitions. Post the list to the forum. Then we can figure out if we can boot Windows using grub.

---

### Post by J Caffrey on 2008-02-04
This is what I got: Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x379c7acb

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         637     5116671    2  XENIX root
/dev/hda2   *         638        2614    15880252+   c  W95 FAT32 (LBA)
/dev/hda3            6081        7296     9767520   83  Linux
/dev/hda4            5899        6080     1461915   82  Linux swap / Solaris

Partition table entries are not in disk order      Does this help?

---

### Post by dstew on 2008-02-04
Yes, that helps a lot. Now post the result of the command```
cat /boot/grub/menu.lst
```

---

### Post by J Caffrey on 2008-02-05
This is what I got,sorry about the delay in replying(the joys of night work)

## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a111e626-df3f-4d9b-adb8-9ab6aea03087 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a111e626-df3f-4d9b-adb8-9ab6aea03087 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by dstew on 2008-02-05
This is the final step. From the ubuntu desktop, open a terminal, and enter the command```
gksudo gedit /boot/grub/menu.lst
```This will allow you to edit the file. At the bottom of the file, below the title Windows NT/2000/XP, change```
root (hd0,0)
```to```
root (hd0,1)
```Save the file, quit the editor program and reboot. Hopefully, the Windows entry on the grub menu will work properly now.

---

### Post by J Caffrey on 2008-02-05
That worked a treat:):)windows is now munching its way through never ending updates.I'll have my Children ubuntu converts by the summer.Many thanks for all your help.

---

### Post by J Caffrey on 2008-02-05
I'm not finished yet.The xp partition was very small so I used my trusty Partition commander to enlarge it.Strangely whenever I reinstall xp the file system is FAT32 so I converted it to NTFS using the xp facility.System commander took over the multiboot and wouldn't boot ubuntu,it kept reporting an error.I uninstalled system commander thinking that normal service would be resumed.Ha no such luck!!! The system now boots straight into xp without showing any multiboot screen,any suggestions please?:(

---

### Post by dstew on 2008-02-05
You will need to re-install the grub boot loader on the Master Boot Record (MBR) of the boot disk. I assume you haven't changed your partition order, but just to be on the safe side, we need to check them again. Boot an Ubuntu Live CD, open a terminal, and enter```
sudo fdisk -l
```If you get the same partition order as before, where /dev/hda2 was your Windows partition, and /dev/hda3 was your Ubuntu Linux partition, then go ahead an reinstall grub as follows. If the partitions are different, post the result to the forum.

To re-install grub do these steps. First, from a Live CD system, open a terminal window and enter the command **grub**. At the grub> prompt, enter these commands:```
root (hd0,2)
setup (hd0)
quit
```Shut down the Ubuntu Live CD system, remove the CD, and boot from the hard disk. It should give you the Ubuntu menu.

---

### Post by J Caffrey on 2008-02-06
The first command works and shows the disc as being unchanged.I just wrote in grub in the terminal window and after a few seconds "grub>" appeared without the inverted commas.I then wrote in root (hd0,2) but I then get "Error 21: Selected disk does not exist" My beginner status is showing:confused:

---

### Post by J Caffrey on 2008-02-06
I checked the disk and it is unchanged so I put in grub.When I put in root (hd0,2) I get error 21 Selected disk does not exist

---

### Post by mysticrider92 on 2008-02-06
Try running grub off of the live cd like before, except type:
> find /boot/grub/stage1

This command will output something along the lines of (hd0,1). Substitute this (hd*) in the "root" command, then follow the other steps.

[edit] By the way, Grub numbers your hard drives starting from 0. (hd0,0) is the first partition of the first drive. The first 0 shows the drive number, and the second one shows the partition. That should help you understand this a little better.

---

### Post by bwtranch on 2008-02-06
finally got my ubuntu 7.10 installed correctly having managed the partitions properly.In the long and laborious process I crashed my XP.I reinstalled it from the backup discs into the second partition but it doesn't show up in the multiboot menu.I have Partition Commander which shows the complete drive asartition(0)recovery,partition(1)WinXP)(free space) partition(2)ext3 Linux and then the swap file.How do I enter XP asI have young Children who can only use XP
__________________

Well, we should raise 'em up right using a Linux system.  The first thing I would do is fire up fdisk gparted doesen't do it for me. Hit p for the partitions that you currently have that is, fdisk /dev/sda or /dev/hda depending on whether you have IDE or SCSI.

Now, make the first part a boot disk and set it to 32 or 64M. The second one should be swap and 512M should be ok for that and then it's up to you the remainder. You have to tell GRUB what you did and really you should go to their site for the naming conventions.

Actually, it occurs to me that if you really don't know what you are doing. Don't mess with it! You should have a backup file for everything that is important! Do you know how to do that? If you are A Windows user, probably not. 

I'm really having second thoughts about writing this post. I don't want you to mess your system up and I don't think you know enough about Unix to handle it. I'm really thinking about deleting the whole thing, but I guess I'll send it.

---

### Post by J Caffrey on 2008-02-06
find /boot/grub/stage1   I did that but got Error 15 file not found.Any more suggestions please? BWTRANCH you are not very helpful thats why this forum is called "Absolute Beginner Talk" are you here to gloat???(its not appreciated)

---

### Post by dstew on 2008-02-06
Try this. Boot a live CD, open a terminal window, and start grub again. At the grub> prompt enter```
root (
```and then hit the Tab key. This takes advantage of the grub command line auto-completion feature to give you a list of the partitions as grub sees them. Post the result to the forum.

---

### Post by J Caffrey on 2008-02-06
root (   I put this in on the grub screen but nothing happened.The cursor moved to the right side of the open bracket like its waiting for a further command.

---

### Post by dstew on 2008-02-06
Did you press the space key or the tab key?

---

### Post by J Caffrey on 2008-02-06
Sorry I was out,I definitelty pressed the tab button.

---

### Post by mysticrider92 on 2008-02-06
Is your main Ubuntu partition mounted on the live cd? If it is, open nautilus and browse to it. Check inside the /boot folder for the grub folder (/boot/grub/). Inside that folder should be around 10 files. Just make sure they exist, and have names like the ones in the attached screenshot.

It sounds like those files are either missing or corrupt, which is odd, but possible.

---

### Post by J Caffrey on 2008-02-12
Couldn't get the grub screen back so I wiped the ext3 partition and the swap file and reinstalled ubuntu.Alls going well now.If only I could get some sound:(:(

---

### Post by Nirevus on 2008-02-12
What's the problem with the sound? Is there a post elsewhere about it?

---

