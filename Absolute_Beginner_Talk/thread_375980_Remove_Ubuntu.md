---
title: "Remove Ubuntu"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Whitecloud on 2007-03-04
Here is what I have done
I have set up two Towers and one Monitor

# 1 Tower has Windows Media Center on it. This is the main Tower. 

# 2 Tower has Ubuntu 6.06 installed. This was a clean install , and that is all that is in this Tower. Ubuntu.

Now I have set up a Belkin PS/2 Flip Switch which I can go from one Tower to the other Tower. With no problem

Now for my question:
On the # 1 Tower is  Windows O/S and Ubuntu O/S  I was rebooting in order to switch the O/S I wanted.
I would like to remove Ubuntu from this Tower.
Can I get some suggestions on doing this.
It has a Grub set up and it is like this.

Gnu Grub version 0.97 (639K lower / 1037544K upper memory )

Ubuntu Kernel 2.6 15-28-386
Ubuntu Kernel 2.6 15-28-386 recovery mode
Ubuntu Kernel 2.6 15-28-386
Ubuntu Kernel 2.6 15-28-386 recovery mode
Ubuntu memtest86+
Other operating systems:
Windows XP Media Center Edition
Windows NT/2000/XP

Use the ( up arrow ) and ( down aroow ) keys to select which entry is highlighted.
Press enter to boot the selected O/S "e" to edit the commands before booting,or "c" for a command-line.

The above is what the opening page shows. Is there something in there that I should click on to remove Ubuntu and go back to just Windows.
I don't think I need Unbuntu on the main Tower anymore. Seeing I have it loaded to its own Tower.

---

### Post by moshuptrail on 2007-03-04
If you want to completely hammer Ub. from T1, then you have two steps:
1. do something with all the partitions to give them back to sindows
  easiest: format them as fat32
2. do a fdisk /mbr and it will wipe grub out completely leaving just the XP boot

---

### Post by Whitecloud on 2007-03-04
> **moshuptrail said:**
> If you want to completely hammer Ub. from T1, then you have two steps:
1. do something with all the partitions to give them back to sindows
  easiest: format them as fat32
2. do a fdisk /mbr and it will wipe grub out completely leaving just the XP boot

Sounds good. Can you explain in simple terms ,how I can do this. I'm not that good with going into the registery

---

### Post by moshuptrail on 2007-03-04
I think the easiest way to format the Ubuntu partitions would be to boot the Live CD.  Better yet, d/l and burn the Gparted LiveCD and boot that.  Either will allow you to run Gparted.  (Gnome Partition Editor)
That has a fairly nice GUI interface that will let you see all the partitions and reformat the ones you need to.
If you are not sure, look at the file /etc/fstab on the Ubuntu installed on T1.  It should tell you which partition is which.  You will probably be able to tell just by the size in Gparted, but it would a good idea to double-check with the fstab file that was in use.  BTW, Gparted will also let you delete the Ubuntu partitions and replace them with a single large partition.  That would be a good thing to do if you feel confident.

To do a fdisk /mbr, you'll need DOS prompt.  I don't think you can do it from command line in a running system (try it, it can't hurt), so you might need a bootable windows disk.  Got a bootable CD around?  That would be best.

Lastly, you may need to format the fat32 partion(s) again from Windows. You can do that from a command line, but you'll need to know the drive letter.

---

### Post by PinkFloydYoshi on 2007-03-04
What is the name of the Ubuntu drive? hda?

Before you start, make sure you have a DOS disk or a Windows 98 CD, unless there's a way to do it in Linux, and if there is, I don't know it yet. Feel free to add to this if there is. :)

Also, if anyone believes any of this is wrong, or there's a better way, feel free to correct me.

Boot up a Ubuntu live CD, bring up a terminal and type this into Konsole:

```
sudo fdisk /dev/hda
```

Your result will be this:

```
pinkfloydyoshi@firaga:/$ sudo fdisk /dev/hda
Password:

The number of cylinders for this disk is set to 4865.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):
```

Press 'P' to list the partitions on your drive. You'll get something similar to the following:

```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4678    37576003+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris

Command (m for help): 
```

This is a box of mine that is dedicated Kubuntu Edgy, so there are no NTFS/HPFS entries, which is what your Windows partition will be. You absolutely don't want to destroy the NTFS/HPFS partition else you will lose your Windows installation. The beauty of fdisk for Linux is that changes aren't committed until you type 'w', then press enter, at that point, changes are made to the drive, and there's no going back, so each time you alter something on the drive, make sure you type 'p' then press enter to view the changes you are making to make sure you're doing what you're setting out to do.

Now you understand that, you're ready to remove your ext2/3 and swap partitions. If you're not booted into a Ubuntu Live CD, make sure you are, else your box will panic if you remove the / partition while the base system is mounted and live.

Look at the output of 'p'. Each entry denotes a number, it doesn't say, but the first entry is partition number 1, second is 2, etc...

If you installed Windows before installing Ubuntu on this box, your Windows partition will be first in this list. Look at the end of the entry and make sure it says NTFS/HPFS. If that is entry number 1 (Partition number 1) then you know **not** to type 'd' (for Delete), then '1' to remove the Windows partition. The others can be removed, so type 'd', then '2', then 'd' again, then '4' to get rid of the swap partition. If there was an Extended Partition (As shown in my drivelist), you can now get rid of it by doing 'd', then '3'. Remember you can't remove the extended partition until you get rid of the swap partition.

Press 'p' again to make sure that the only entry left is the NTFS/HPFS partition. Should look a little like this:

```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4678    37576003+  83  NTFS/HPFS

Command (m for help): 
```

If so, now is the time to write changes. If not, type 'q' to exit and then restart fdisk by doing 'sudo fdisk /dev/hda'. Otherwise, type 'w' (Write changes), then press enter. This will finalize all the changes you made and will destroy the partitions that you removed during it, leaving the one Windows partition on the drive so you can boot back into it.

Thats the hard part out the way. Now you can grab a Windows 98 CD of a DOS disk and boot it into a command prompt. Once booted, type in fdisk /mbr. Now you've done that, grub is no longer on your drive. 

Final step. Now you need to make your Windows partition 'active', else your machine won't boot back up. Type in fdisk, then press enter. In this DOS version of fdisk, changes you make take effect immediately, so just remember you need to make your Windows partition active and nothing else. It'll give you a huge wad of text, basically telling you "Your computer has a disk larger than 512Mb". Answer 'Yes' to "Do you want to enable large disk support?". It'll give you 4 choices. You want the second choice: "2. Set Active Partition" so press 2 then enter. Select partition 1, then press enter. You're done. Press ESC to exit and reboot. Your box should now boot back into Windows.

Enjoy.

---

