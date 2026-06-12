---
title: "How do you format CF cards?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-08-11
I have been at this problem for a while and still can't figure it. I have a Microtrack recorder with a compact flash card. Gparted couldn't even see it! So now I have it in my camera, and gparted can see it, but ONLY when it is mounted. And it seems to give no option to format it. "Disks Manager" cn see it whether it is mounted or not, and gives no opition to format it either way! When it is unmounted, under the partitions ta b it simply says "There aren't known partitions in the disk".

I have tried fdisk, which is daunting as I must use the terminal. I see no option there also for formating it. How on earth does one use anything for formatting it? Some people said fdisk, but, HOW?

For a sample of my attepts, here is copied from the terminal:

justin@justin-laptop:~$ fdisk /dev/sda

The number of cylinders for this disk is set to 7872.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): p

Disk /dev/sda: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7871     2014960    6  FAT16

Command (m for help): d
Selected partition 1

Command (m for help): d
No partition is defined yet!

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
n
Invalid partition number for type `n'
Command action
   e   extended
   p   primary partition (1-4)
d
Invalid partition number for type `d'
Command action
   e   extended
   p   primary partition (1-4)
d
Invalid partition number for type `d'
Command action
   e   extended
   p   primary partition (1-4)
l



I just want to make the whole thing FAT32. Help much appreciated
Thanks
Justin

---

### Post by frrobert on 2006-08-11
Justin,

My guess is that to format the card the card would have to be in a card reader.  By being in your recorder or your camera that item has control over formating.  Can either the recorder or the camera reformat the card?  That may be the easiest route.

---

### Post by woodlandjustin on 2006-08-11
The cameraq can reformat the card in its own way. The Microtrack can USUALLY format cards, but sometimes they come preformatted in a particular way which makes the Microtrack unable to reformat them. Their webpage says in that event, you plug in the microtrack to your computer and click on "format card" (basically. It gives very easy lookig instructions to do that on both mac and  Windows. Seems infinitely complex here on linux though.)

---

