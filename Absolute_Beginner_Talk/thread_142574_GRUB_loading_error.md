---
title: "GRUB loading error"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by Felix21685 on 2006-03-10
hey guys

this is what happend today on my 2nd computer,

i just removed the cd from the drive so ubuntu can go on and do its thing

this is what happens right after reboot.

GRUB Loading stage1.5ReadError


any clues?
i used this same setup BUT a different drive and it worked.
now i put a WD 120GB 8mb cache and it doesnt work.
any help is appreciated

---

### Post by Pragmatist on 2006-03-10
stage1.5 loads filesystem support so my guess is that the problem is with the filesystem type on your partition.  You need to boot from a boot disk or LiveCD, get to a prompt and type: ```
fdisk /dev/hda
``` assuming /dev/hda is the hard drive that you installed Linux on.  Write the information down and give it to us here.  My favorite choice is to use **Knoppix** which, since you have a second computer, you can easily download from: [http://www.linuxiso.org/](http://www.linuxiso.org/)

---

### Post by Felix21685 on 2006-03-14
root@0[knoppix]# fdisk /dev/hda

The number of cylinders for this disk is set to 14593.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): 
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

Command (m for help):   
root@0[knoppix]# 

what should i do now? is it right is it supposed to be the knoppix root?

---

### Post by Pragmatist on 2006-03-14
type **p **At the prompt  **Command (m for help):**

---

