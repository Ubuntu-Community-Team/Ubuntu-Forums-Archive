---
title: "VirtualBox - how to create virtual disk image from factory &quot;Recovery&quot; partition"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2007-07-17
I must be missing something here.  I installed VirtualBox (innoTek ver. 1.4.0) using Automatix.

I am trying to get VirtualBox to run the Hp Recovery partition on my hard drive.  It of course has a bootable setup ready to go.  It is FAT32, around 8 GB, and it is mounted in my Ubuntu.

I can get VirtualBox to boot to a CD with a setup program, such as the good old Windows XP installation CD.

But I need to make a virtual disk image of that FAT32 HP Recovery partition, and despite my reading I am unclear on how to do this.  If I can do that, then I can point the Virtual Disk manager to that saved image file, and VirtualBox will boot it.  (I guess.)

I guess what I find funny is that the entire FAT32 HP Recovery partition **is** a bootable image with a setup.

I appreciate any guidance.  The docs reference the use of VMDK image files (from other virtualization software) and also raw host hard disk, but before I jump into that maybe someone reading this knows of a better way.

THANKS !!!

---

### Post by scott_g on 2007-07-17
I have a recovery partition similar to this, and would be interested in a fix.

However, I don't think this will work; when the Recovery HD boots, it checks the BIOS.  Because the BIOS of virtual box is not the same as your computer's, the Recovery HD reports that it is in a new computer, and thinks you are trying to use it as a windows install disk.

You can try it by making the recovery disks, and trying to get Virtual Box to boot off the disks.

Scott

---

