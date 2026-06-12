---
title: "Problem with chainloading"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Yoke &amp; Chung on 2008-01-02
Hi,

I have recently installed PCLinuxOS to my IDE slave hard disk, and bootloader (using grub) was installed onto the same hard disk as well. Now, I have a problem chainloading the grub.

Here is my hard disks setup:

1. SATA channel 1: Primary master SATA drive-- sda1: Windows XP, sda2: Xubuntu 7.10
2. IDE channel 1: IDE master drive-- hdc1: ext3, to store backup images of sda2. 
3. IDE channel 1: IDE slave drive-- hdd1: PCLinuxOS <-- this drive is newly installed to test other Linux distros.

There is no hda & hdb, I guess it is because I have used the IDE channel 0 for my DVD-RW drive.

I can bootup to PCLinuxOS fine if I set my BIOS to boot from the IDE slave drive. However, I would like to chainload PCLinuxOS directly from the grub menu instead of keep changing my BIOS settings.

I have added the followings to the grub menu (/boot/grub/menu.lst):

title PCLinuxOS
rootnoverify (hd3,0) <-- this is the confusing part, is this the correct number to use? 
chainloader +1

The error message from grub is bootloader not found. I tried switching from (hd3,0) to (hd2,0), and error message came out too when I select "PCLinuxOS" from the menu.

Or should I copy and add the whole chunk from PCLinuxOS grub menu to the Xubuntu grub? I saw the grub configure PCLinux partition as (hd0,0), and afraid this might conflict with Xubuntu and Windows XP.

I checked the Xubuntu grub setup, and sda1 is represented by hd0.

Thanks in advance.

---

### Post by jken146 on 2008-01-02
Which OSs can you currently boot to?  Which does the most recent install of GRUB belong to?

Boot into that OS and post the output of these 2 commands please:
```
sudo fdisk -l

cat /boot/grub/menu.lst
```

---

### Post by ~LoKe on 2008-01-02
Boot into linux however you can, then open up a terminal and type:
```
sudo fdisk -l
```
And give us the output.

I can't remember the logic behind hd(x,x), but you might need to try hd(3,1) or an odd combination.

---

### Post by jken146 on 2008-01-02
The logic behind (hdx,y) is this:

x is for the hard drive.  Start counting from 0.  x=0 means hda.

y is for the partition.  Start counting from 0.  y=0 means hdx1.


For example, (hd2,3) means the fourth partition on the third disk, i.e. hdc4.

---

### Post by ~LoKe on 2008-01-02
Oh, that's right.  I kept forgetting 0 was the first, I keep thinking 1=1 (I blame Windows).  That explains why I could never figure it out. ;)

---

### Post by marx2k on 2008-01-02
Also it's:

"cat /boot/grub/menu.lst"

---

### Post by jken146 on 2008-01-02
> **marx2k said:**
> Also it's:

"cat /boot/grub/menu.lst"

Thanks for pointing that out.  Grrrr, typos will be the death of me!

---

### Post by Yoke &amp; Chung on 2008-01-02
> **jken146 said:**
> Which OSs can you currently boot to?  Which does the most recent install of GRUB belong to?

Boot into that OS and post the output of these 2 commands please:
```
sudo fdisk -l

cat /boot/grub/menu.lst
```


I will try that later when I am home, thanks.

---

### Post by Yoke &amp; Chung on 2008-01-02
> **jken146 said:**
> The logic behind (hdx,y) is this:

x is for the hard drive.  Start counting from 0.  x=0 means hda.

y is for the partition.  Start counting from 0.  y=0 means hdx1.


For example, (hd2,3) means the fourth partition on the third disk, i.e. hdc4.

How about SATA drive? The grub configure my SATA partition (sda1 & sda2) as (hd0,0) and (hd0,1) respectively.

In my case, I do not have hda & hdb, will double check again using fdisk as suggested by helpful posters. The partition PCLinuxOS is sitting on is recognozed as hdd1 by Xubuntu. So, I put (hd3,0) in the grub menu, but it seems like not working. 

Will post more information when I am back home and do the fdisk command. Thanks everyone!

---

### Post by Yoke &amp; Chung on 2008-01-07
This issue is temporary closed, as I need to re-install PCLinuxOS. 

I screwed that up during an installation of driver for nVidia 8600 GTS on PCLinuxOS. Instead of re-installing PCLinuxOS, I  might try KnoppMyth :)

Thanks everyone for your quick response.

---

