---
title: "Advice on fresh install"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by phiellaep on 2006-12-10
Hello,

Having just gone through hell to get my system back after a bad install of Ubuntu (my own silly fault), I am willing to try it all again!

But this time I'm going to request some advice on the rpocedure involved.

My setup:
2 Hard Disks, Both Unpartitioned.
1st HDD contains Windows.
2nd HDD contains files, backed up things, and no OS.
Only OS installed just now is Windows.

I would like to be able to install Ubuntu on my first HDD, alongside windows, and leave my second HDD untouched and uninvolved in the entire process.

When I first installed Ubuntu, the time things went bad, my procedure was this (maybe someone can spot where I went wrong): I used the ubuntu love cd to launch ubuntu. I then ran the install programme and partitioned my first hdd (the windows one) to acomodate 20 gigs for ubuntu and 4 gigs for the linux swap (is 4 gig too much?). When GRUB was being set up, I went with the default option which was hd0.

Upon reboot, the system went straight to windows. Evidently GRUB was not set up correctly. Any ideas why this is?

So, in my silly logic, I thought "well, hd0 is obviously wrong, I'll set it up on hd1". I installed GRUB to hd1. Upon reboot, the GRUB screen appeared! But none of the options, including windows, worked. They all gave errors such as 'device not found' etc.

I tried to rescue my windows by using the Win XP recovery console and commands such as fixmbr etc. This did not work!

I had to format everything and start afresh.


So,
What is the correct procedure, and why did installing grub to hd0 not work?

Thanks in advance,

Philip

---

### Post by riven0 on 2006-12-10
The best way to do a dual-boot install, is first to install Windows. Windows is a bully and likes having the whole hd for itself.:mrgreen: 

After that, boot up the Ubuntu LiveCD, partition the hd from there, (make sure you put Ubuntu *after* Windows!), install and restart. Ubuntu should automatically recognize windows and update the grub accordingly.

---

### Post by bulldog on 2006-12-10
The most important thing,when you have more than one disk,is to see which one is set to boot by default.
This would be disk (hd0) than the other one is (hd1)

If you make a swap about 1GB it's enough.

Try to reinstall and if grub not appears,**don't** wipe out everything,it can be easely restored!!

---

### Post by phiellaep on 2006-12-11
but how come when i installed grub to hd0 it didnt work?

---

### Post by bulldog on 2006-12-11
It depends.if you have only IDE disks it should appear,but if you have Sata it's another story,because both disks are set as master.

The best way to make a dual boot machine is ubuntu on the default boot device with GRUB in the MBR and windows on the slave disk.
You have to change some things in GRUB but that's easy to do.

This way you can boot ubuntu and windows with GRUB,but if things should go wrong with GRUB,you can always boot windows by changing the boot device in your BIOS.

---

### Post by phiellaep on 2006-12-13
ah!

my main hdd is sata, and my backup is ide.

does that explain these goings-on?

---

### Post by bulldog on 2006-12-13
Yes,they're both masters I suppose.
On some computers the IDE disk comes before the Sata in terms of ranking.

But you can reverse them in your BIOS by choosing the Sata as first boot device.

---

### Post by az on 2006-12-13
> **phiellaep said:**
> but how come when i installed grub to hd0 it didnt work?

Grub uses the information that the BIOS gives it to map the drives.  You can change the drive map in the grub configuration in /boot/grub

Install again and use hd0

Then, before you reboot, you will have to mount the partition and map hd0 to hd1 and vice versa.  That is if changing the boot order in your bios does not work.

This is the result of a (usually) buggy bios which does not provide the correct information to grub.  That's why you need to work-around the problem by hand.

---

