---
title: "installing grub and editing fstab"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Liet_Kynes on 2008-02-10
When I installed ubuntu I had 2 sata HD in my pc. I installed grub to the mbr of the 1st HD. I have since removed the 1st HD and now would like to install grub to the mbr of the 2nd HD(the only 1 now).

How do i do this?

Also the drive numbering would now be different for my filesystems if i understand it correctly. (sdb1 would now have to be sda1). I don't think I will have a problem with that but  I'm currently unable to boot without a bootloader/manager.

Any suggestions for how to proceed?

I've tried the suggestions of some of the posts here by running the live-cd.
Typing :  grub
and then locate /boot/grub/stage1

but it tells me not found.

---

### Post by logos34 on 2008-02-10
it's 

sudo grub

**find **/boot/grub/stage1

Use [this guide]("http://ubuntuforums.org/showthread.php?t=224351").

Yes, you need to edit menu.lst.

> sudo mkdir /media/ubuntu

sudo mount -t ext3 /dev/sda1 /media/ubuntu 

sudo gedit /media/ubuntu/boot/grub/menu.lst

Change the 'groot' and 'root' line to (hd**0**,0).

---

### Post by Liet_Kynes on 2008-02-10
> **logos34 said:**
> 

sudo grub

**find **/boot/grub/stage1

Use [this guide]("http://ubuntuforums.org/showthread.php?t=224351").

Yes, you need to edit menu.lst.



Change the 'groot' and 'root' line to (hd**0**,0).


Thanks sudo made a big difference :)

BTW What groot?

---

### Post by logos34 on 2008-02-10
> **Liet_Kynes said:**
> Thanks sudo made a big difference :)

BTW What groot?

short for 'grub root'.   It tells grub-update (i.e. kernel update) where to look for the kernels (it comes into play in the event you have a separate /boot partition).  But yours should be the same as root, hd0,0

---

### Post by Liet_Kynes on 2008-02-10
> **logos34 said:**
> short for 'grub root'.   It tells grub-update (i.e. kernel update) where to look for the kernels (it comes into play in the event you have a separate /boot partition).  But yours should be the same as root, hd0,0

So it's not necessary to change if you installed to only 1 partition?

---

### Post by Liet_Kynes on 2008-02-10
My system is up and running again. For some reason it is very unresponsive though? What could have gone wrong?

---

### Post by rkd on 2008-02-10
You should be sure the location given on the root command and the location given on the #groot command are the same. When a kernel update is done, it uses #groot to redo the settings, and if #groot isn't right, the root setting will be wrong after a kernel update.

---

### Post by Liet_Kynes on 2008-02-10
In my menu.lst the groot sections are commented out.?

---

### Post by rkd on 2008-02-10
Yes, the #groot line is a comment line, which means that Grub itself is not using it. But when Ubuntu does a kernel update, one of the programs used then reads menu.lst and uses some of those lines within the comments to control the creation of a new menu.lst, and *that* is when the #groot line is used.

So if you don't change it now, things will work fine now, but the next time the Ubuntu updates have a kernel update in them, after you apply that set of updates, your menu.lst will be wrong, and you might not be able to boot until you edit menu.lst by hand.

Perhaps it isn't the best way for things to be set up, but that's how it has been done.

---

### Post by geo909 on 2008-02-10
For grub installation issues, you might want to check "super grub disk".
It is supposed to restore grub automatically and do many other related things...
I haven't tried to say for sure.

---

### Post by spiderbatdad on 2008-02-10
you may also be interested in "disk manager"

---

