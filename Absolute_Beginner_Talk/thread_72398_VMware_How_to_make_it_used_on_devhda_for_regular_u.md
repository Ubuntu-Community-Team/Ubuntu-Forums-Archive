---
title: "VMware: How to make it used on /dev/hda for regular users without sudo vmware ?"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-06
VMware: How to make it used on /dev/hda for regular users without using the  sudo vmware ?

Is there a way to give possibilty of using the physical harddisk /dev/hda without being root or doing sudo ?

thanks a lot

("vmware -superuser"  maybe ?)

---

### Post by brentoboy on 2005-10-06
im not sure i understand what you want it to use from /dev/hda

I certainly wouldnt recommend letting vmware have root access to your entire hard drive.

that would be bad.

---

### Post by patrick295767 on 2005-10-06
[QUOTE=brentoboy]im not sure i understand what you want it to use from /dev/hda
I certainly wouldnt recommend letting vmware have root access to your entire hard drive.
that would be bad.[/QUOTE]


Hi, 

(I have a disk with 4 partitions : fat16, windowsnt, data_disk_ntfs, linux+swap )

i tried to use the vmware as regular user ($) (not root)
but the vmware is telling me that it cannot access the physical harddisk /dev/hda (cos of rights).
Unfortunaltly, I have to do so (use the vmware for whole /dev/hda harddisk) otherwise, if I use vmware on only one partitions or two partitions (ntfs), I got the error message 
Grub Loading 
Error 17
So, the only way i found was to use the physical harddisk /dev/hda, to do vmware of my windows ntfs partition. 
If you have additional information concerning the vmware and its use with one or 2 ntfs partitions (os nt and data), please let me know how to do this. 
Thanks 
Pat'

---

