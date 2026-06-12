---
title: "Grub Boot issues"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by grzbear on 2006-10-15
I have just built a new machine: AM2 socket. AMD64 X2 4600 and 4 sata drives.  Ubuntu loaded and worked fine, and still does.  However I must use the install CD to boot from the SATA drive now after upgrading the kernel from 2.6.15-26-amd64-generic to 2.6.15-27-amd64-generic.

When I boot without the CD all I get is a blinking cursor... not even an attempt to get into Grub.  I have tried to re-nstall grub.

I installed Ubuntu on sda1 swap is in an extended sda2 partition as sda5.

I have read a number of threads on this issue and have also tried a number of the suggestions.

sda is listed as (hd0) in /boot/grub/device.map

root is (hd0,0) in /boot/grub/menu.lst

](*,) 

I am thinking that resolution at this point may be to go back to a fresh install and forget about the kernel update.

TIA for any helpful thoughts towards a resolution.

grz

---

### Post by ciscosurfer on 2006-10-15
Perhaps the link in my signature can help you out.

---

### Post by grzbear on 2006-10-15
I have read through the Grub pages and tried everything I could think of on this page... apparently Grub is installed and set up properly.

When invoked from the Ubuntu install CD Grub seems to work and load as it should.  When booting without the CD, it is as if the MBR is not recognized on boot up and I get the blank screen with a blinking cursor.

This occured with the update of the new kernel to initrd.img-2.6.15-27-amd64-generic from initrd.img-2.6.15-26-amd64-generic

It was fine before the upgrade through system update.

Thanks for your link, though.  It could come in handy.

grz

---

### Post by anaconda on 2006-10-15
My guess is that your grub is installed to wrong SATA drive.. for some reason bios boots first to a SATA hd, which hasn't got grub installed to its mbr.

remove all other SATA hard-disks (not the ubuntu one) and check if it works..

If that was the problem, then change the SATA cables so that the one with ubuntu (or grub in mbr) is the first..

In my machine grub automatically guesses that the IDE-drive is the primary drive, but BIOS boots from my SATA hd first...

EDIT: you can also install grub to the mbr of each disk to make sure that grub is loaded...

---

### Post by grzbear on 2006-10-15
My drives appear to be set up in the bios correctly; no ide hd in system.

I did what you suggested and the machine booted... I am going to try it again and then with the drives connected.

I may do as you suggest and install grub in each MBR...

Thank you!

I find this interesting.

grz

---

### Post by grzbear on 2006-10-15
It is working now... this is what I did.

I disconnected all but the Ubuntu sata drive and booted... shut down and added scond drive and booted and then did the same with the following 2 drives.

Each time Ubuntu started up just fine.

ODD :-k 

grz

---

