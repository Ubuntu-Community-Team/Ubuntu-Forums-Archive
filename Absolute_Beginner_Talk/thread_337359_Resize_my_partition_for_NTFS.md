---
title: "Resize my partition for NTFS"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by darkcyber on 2007-01-12
Ok, I finally got ubuntu installed and I did the manual partition thing and slide the slider bar all the way to the left for it to use the least amount of my free space, but it use ALL of my free space.  Now when I boot into Windows XP it shows I have 200 mb's of free hd space.  How can I resize the ubuntu partition and recover that free space for my Windows XP partition.

Total noob here...so in depth instructions would help.  

I have a 34 gig SATA raptor and here's what windows is showing:

Windows partition is 13.56 gigs, ubuntu partition is 20.03 and the 902 mb I guess for the ubuntu swap partition.

I need to take space from that 20.03 and put it back on that 13.56 partition.

Thanks!

---

### Post by logos34 on 2007-01-12
Here are some good step-by-step instructions:
[Resizing partitions with GParted]("http://gparted.sourceforge.net/documentation.php")

Download the Gparted livecd and use it instead of the version on the install cd.

---

### Post by darkcyber on 2007-01-12
> **logos34 said:**
> Here are some good step-by-step instructions:
[Resizing partitions with GParted]("http://gparted.sourceforge.net/documentation.php")

Download the Gparted livecd and use it instead of the version on the install cd.

Thanks very much for link very good information there.

---

### Post by darkcyber on 2007-01-13
Ok, if I use Gparted, I know I can resize the partitions, but once I do that is there a way I can add the free space back to my Windows ntfs partition?

---

### Post by bodhi.zazen on 2007-01-13
yes, just reverse the process ....

However the free space must be adjacent, to  the left of your ntfs partition and not following the ubuntu partitions.

Perhaps make a data partition to share between windows and ubuntu ?

---

### Post by darkcyber on 2007-01-13
> **bodhi.zazen said:**
> yes, just reverse the process ....

However the free space must be adjacent, to  the left of your ntfs partition and not following the ubuntu partitions.

Perhaps make a data partition to share between windows and ubuntu ?

How do you reverse the process?  You mean use gparted and resize the linux partition and then take the free space and add it to the ntfs partition?  Other than that, I don't know what you mean by reverse it.  Because ubuntu created these on installation.

---

### Post by bodhi.zazen on 2007-01-13
I do not understand what you are trying to do exactly .....

Are you deleting Ubutu and restoring your free space to NTFS ? If so, delete all the non-ntfs partitions and add the free space to the ntfs by re-sizing the ntfs partition....

If however your partition table is something like ..

hda1 ntfs
hda2 ubuntu
hda3 swap
free space

it will be difficult to move the free space to the ntfs partition. You will need to resize/move the partitions so you have:

hda1 ntfs
free space
hda2 ubuntu
swap

You can then add the free space to ntfs...

Which is why I suggested a shared data partition.

In addition you can not move free space from an extended partition to a primary partition ...

could you post your current partition table

sudo fdisk -l

and what you want it to be ??

---

### Post by darkcyber on 2007-01-13
Thanks for the help everyone!!!   GParted worked wonderful...got it all fixed up now! :-D

---

