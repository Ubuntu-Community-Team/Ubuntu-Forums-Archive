---
title: "Keeping XP -how can I add linux as an additional partition?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by numerical on 2007-03-26
Hello everybody,


I would like to be able to choose from LINUX OS or my existing WIN XP OS from the boot menu when I turn the power on,on my labtop. The question i cant figure out is :How can I create a new (linux OS)partition on my existing hardrive (WINXP) and make that new partition a LINUX OS so i can boot up whichever one i choose>?

I have already downloaded : instluxNETUbuntu5_10_en.exe from sourceforge.net 

and when I run it :it says unable to mount.

What must I do to keep my current Windows OS(and data therein) and still have the ability to boot up LINUX upon restart.I would really like to be able to run both ,does anybody know excatly how to do this?

Thanks
Numbers

---

### Post by thefoolisme on 2007-03-26
Not sure what the .exe file is that you downloaded.  I used the .iso file from ubuntu.com.  Download and burn to a CD at a slow speed, or else you may end up with errors.  Be sure to backup up your windows files, and defrag the hard drive.  

After that's done, put the ubuntu CD into your drive, and reboot.  Select check disk first to make sure you don't have any burning errors, then select run/install.

After a few setup questions, you will come to the partitioning questions.  You can have it resize your Windows partition and set up a new partition and install Linux on that largest available space (which since you defragged, would be pretty easy for gparted to find).  GRUB will be installed, so that you can choose which OS you want to work with.   It's pretty easy, and there are plenty of guides out there to get you through it.

---

### Post by dropshot on 2007-03-26
The Ubuntu installation has a partition manager. Use it to resize your winxp partition to something smaller, and use what's left for a partition for Ubuntu.

Ubuntu also comes with GRUB, which lets you choose what OS to run when you boot up.

---

### Post by igknighted on 2007-03-26
I would avoid that windows based installer.  It is really in the experimental stage only.  Download the live CD from [www.ubuntu.com](www.ubuntu.com), then try it out.  It runs from the CD without ever touching your HD.  It will be much faster once on the HD, but you can at least see what its all about first.

The installer is on the desktop of the booted live CD.  Defrag and disk check your windows partition first, then boot the live CD.  The installer can automatically resize your windows partition and install Ubuntu to the new free space.  Then it will install a bootloader called grub that will give you a menu just after your bios POST that will let you pick what OS to boot.  Ubuntu will be set as the default to boot after 10seconds of no activity, but that can be changed.  If you use a USB keyboard make sure this is enabled in your bios.

---

### Post by bulldog on 2007-03-26
Well you should download an ISO first and burn it as  an Image.
[http://www.ubuntu.com/](http://www.ubuntu.com/)
Choose the one you want to have,a suggestion,try Edgy Eft [6.10] it's very good.

Okay when your downloading the next explanation.
To install ubuntu,you'll have to make some free space on your hard disk.
You need about 10GB for a reasonable try out.
The best way to free up space is by using the GParted live cd [30MB] download it and burn it on a cd-r and boot from it.
You will have a nice graphical interface to resize your hard disk.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Let's assume you have freed 10GB with GParted. {more is better,but that's your decision]
Create from this 10GB two partitions.
A 9GB partition and set it to format as ext3
A 1GB partition and format it as swap
Now exit the GParted live cd.

If you have burned the ubuntu ISO as an image,do it on a slow speed for better burning,boot from this cd and take a look around with this live cd,see if your hardware is supported ie. sound,internet and that kind of stuff.
If you're satisfied hit the install button on the desktop.
Go through the questions till you come to the partition part.
Choose manual partition.
Now mount the 9GB partition as /  (root) and set it to format ext3
Mount the 1GB as swap and format it as swap.
Continue the install and all should go fine.

Hope you'll understand all this.

Good luck.

---

### Post by igknighted on 2007-03-26
> **bulldog said:**
> Well you should download an ISO first and burn it as  an Image.
[http://www.ubuntu.com/](http://www.ubuntu.com/)
Choose the one you want to have,a suggestion,try Edgy Eft [6.10] it's very good.

Okay when your downloading the next explanation.
To install ubuntu,you'll have to make some free space on your hard disk.
You need about 10GB for a reasonable try out.
The best way to free up space is by using the GParted live cd [30MB] download it and burn it on a cd-r and boot from it.
You will have a nice graphical interface to resize your hard disk.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Let's assume you have freed 10GB with GParted. {more is better,but that's your decision]
Create from this 10GB two partitions.
A 9GB partition and set it to format as ext3
A 1GB partition and format it as swap
Now exit the GParted live cd.

If you have burned the ubuntu ISO as an image,do it on a slow speed for better burning,boot from this cd and take a look around with this live cd,see if your hardware is supported ie. sound,internet and that kind of stuff.
If you're satisfied hit the install button on the desktop.
Go through the questions till you come to the partition part.
Choose manual partition.
Now mount the 9GB partition as /  (root) and set it to format ext3
Mount the 1GB as swap and format it as swap.
Continue the install and all should go fine.

Hope you'll understand all this.

Good luck.

Gparted is included on the Ubuntu live CD.  Using the separate CD complicates things and can lead to errors (more chances for a bad burn or bad iso file especially).  There should be no issue using the partitioning software on the Ubuntu disc (unless you are using vista, in which case you must use a windows program to resize it).

---

### Post by numerical on 2007-03-26
Thanks Everbody !

I look foward to getting this started ASAP.

I will repost a new thread or add to this one if i have any problems.

Thanks
Numbers

---

### Post by govthos on 2007-03-26
i already have a partition (not my windows partition) I would like to use, will it recognize my windows install without going through the resize process?

In other words I have a 15GB partition for windows and a 40GB partition that has nothing on it.  I would like to install ubuntu on a 14GB partition, have a 1GB swap and still have 25GB for storage.  Would I be able to install ubuntu as my system is configured, and still be able to use XP.  Or, does ubuntu only recognize a windows partition if it resizes the partition it is on.

Thank you for any advise you can give.

---

