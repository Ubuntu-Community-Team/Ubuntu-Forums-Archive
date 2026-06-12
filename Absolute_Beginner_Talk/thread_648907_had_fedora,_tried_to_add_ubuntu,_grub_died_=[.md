---
title: "had fedora, tried to add ubuntu, grub died =["
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by GustavTheLion on 2007-12-24
ey mates, i have had fedora 8 for a while now and i do enjoy it. i used to have xubuntu on one of my older laptops. so i decided to install kubuntu onto the little partition i left of when i installed fedora 8. I went through the install fine until it just stopped suddenly and then shutdown. Now when i start my computer up all its says is "GRUB" and does nothing, no options nothing. And now i cant even boot with my fedora 8 cd, or my windows xp pro cd. I can ONLY boot with ubuntu cd's.

How can i restore the mbr to boot my fedora 8 again, is it possible?(so i can keep all my files, i dont really want to start fresh)

if not, how can i at least boot fedora 8 and resinstall it, or boot windows and install it?

the only way to use my machine period right now is to boot with a u/ku/xu-buntu live-cd

---

### Post by notoriousdbp on 2007-12-24
Depends if you had a separate /home partition.  A re-install of Fedora could be linked to your /home partition with no loss of data.  (I'm only assuming this because I know that Ubuntu can be re-installed in this way and it has got me out of jail on more than one occasion).

---

### Post by Bigbluecat on 2007-12-24
You should be able to restore the your boot. My first port of call for boot issues is Super Grub Disk:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Coupled with the excellent help from Herman:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by GustavTheLion on 2007-12-24
well thanks for the info, my computer does allow me to boot from the super grub disk

i installed GRUB, but to no avail... i can still only boot live cd's of the ubuntu kind

my fedora cd does boot my laptop and a friends computer, so i know the disk is good.

does ubuntu have some defense system i have to turn off?

---

### Post by Bigbluecat on 2007-12-25
I suspect from the first post the Ubuntu install was unsuccessful but got far enough to re-write the MBR (Master Boot Record). I think we should try to get your Fedora back in working order then you can decide if you want to try to re-install Ubuntu.

The MBR as small file at start of your bootable disk. You can think of it as a pointer to where the bootloader can find the configuration files with the into it needs to boot the OS.

If the Ubuntu install re-wrote this to point to it's own partition but the install is not complete then it may fail. Hopefully the simplest fix is to get this pointing to you Fedroa 8 install (I am assuming Fedora uses Grub - I'm not familiar with it).

We can do this from you Ubuntu live CD. 

Once booted open a terminal. We need to find the partition where Fedora resides. So enter:

> sudo fdisk -l

This will give you  list of disk partitions such as /dev/sda1, /dev/sda2 etc.

You need to be able to identify the partition that contains Fedora.

Now - this is important - Grub and Linux number the drive differently. Grub calls  all partitions (hdx,x) where x is a number. The important part is that Grub always starts counting from 0 so Linux /dev/sda1 is (hd0,0) for Grub (first partition of the first drive.

If you know the partition then we are ready to set up grub again.

In the terminal type:

> sudo grub

This brings up the grub command prompt (you see this already when your boot fails).

We then need to tell grub what it's root partition will be. In this case you need to enter:

> root (hdx,x)

where x,x is the location of Fedora.

Then we need to tell grub to re-write the MBR:

> setup (hdx)

If you have only on disk or teh first disk is the boot disk then this will be setup (hd0).

Now we exit grub:

> quit

OK now shutdown and try to boot Fedora normally.

If this does not work we will get a little more involved with Grub and try to manually boot your Fedora install using instructions from Herman (I have done this a few times).

[http://users.bigpond.net.au/hermanzone/p15.htm#cli](http://users.bigpond.net.au/hermanzone/p15.htm#cli)

---

