---
title: "Imaging Drives"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by gavshouse on 2008-04-12
hi i have a 80GB IDE drive split

15Gb for Ubuntu 7.10
15Gb for Windows XP Pro SP2
2GB for Swap
Rest is Ext3 used both in XP & Linux (this content isnt really inportant i can copy this to a ex HDD for now)

ive ordered a 500GB  SATA-300 32mb cahce drive i want to copy that 80gb over to the 500gb for faster boot up etc, now imaging a drive isnt that hard but what with grub installed and dual booting. any ideas ? 

Is there a backup for ubuntu so i can copy everything apps, user data etc. then re-install ubuntu then just restore it. 

So bascily i want to image the drive onto my 500Gb but im not sure what grub would do ? 

the new patitions would be
15Gb for Ubuntu 7.10
15gb for Windows XP 
2GB for swap
Rest is Ex3

i was thiking if i setup the drive the same as the 80gb it would be ok but not sure how grub works any got any ideas ?

---

### Post by Inxsible on 2008-04-12
you need to use the dd command which will perform a bit by bit copy of the source disk to the target disk.

And you are right, you will get the same partitions on the 500 GB drive. But once your copy is done, you can always open GParted and resize the partitions if you wish.

Here's a couple of links to get you started.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

[http://frankmash.blogspot.com/2005/10/dd-how-to-create-bit-for-bit-copy-of.html](http://frankmash.blogspot.com/2005/10/dd-how-to-create-bit-for-bit-copy-of.html)

---

### Post by gavshouse on 2008-04-13
thanks when it comes i will try it out, but might do a full re-install of ubuntu 8.04 not sure.

---

