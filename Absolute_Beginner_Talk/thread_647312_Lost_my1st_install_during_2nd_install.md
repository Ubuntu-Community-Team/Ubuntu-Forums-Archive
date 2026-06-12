---
title: "Lost my1st install during 2nd install"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by uk28 on 2007-12-22
Hi all, i'm totally gutted. 

I've been using Ubuntu 7.10 for a while now without a problem. I was installed on one drive - sda

I attempted to install Fedora 8 on my second drive - sdb, with the option for the boot part to be on the origional sda drive. Presuming it would just override the grub conf and present both OS's. 

Once installed the Grub loader went a bit weird, so i installed another copy of Ubuntu 7.10 on the second drive - sdb to overwrite the grub config and hopefully give me access to my original installation again. 

Well now i do have access to that 'orgional' installation on my first disk. but its a clean copy! everything has gone. It used to have a xen kernal option which has gone, so i'm not sure it really is booting into my old setup or not. 

I've mounted disks and can't find a trace of my old setup. I'm totally gutted. What on earth has gone wrong?

---

### Post by dstew on 2007-12-22
What is the output of **sudo fdisk -l** ?

---

