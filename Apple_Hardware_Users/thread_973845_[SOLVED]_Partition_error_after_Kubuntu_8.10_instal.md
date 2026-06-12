---
title: "[SOLVED] Partition error after Kubuntu 8.10 install"
date: 2008-11-07
forum: Apple Hardware Users
---

### Post by fourth_stooge on 2008-11-07
I have an aluminum iMac (OS version 10.5.5), and recently i decided to install kubuntu 8.10 as dual boot.  I followed the [MacBook directions]("https://help.ubuntu.com/community/MacBook") for the installation, except that i have *not* installed rEFIt  (according to those directions, it should not be necessary.)  Afterwards, i read the ["Intel Macs with Hardy 'No Bootable Devices'"]("http://ubuntuforums.org/showthread.php?t=767677") post, because this issue seems similar, although it's manifesting itself slightly differently.  Perhaps my problem will help you work on the other one.

Basically, the system is not mounting the kubuntu partition.

Instal Procedure:
> 
1.  If necessary, use Boot Camp to resize your OSX partition and make space for Ubuntu. Don't waste a CD creating a Windows driver disk. Reboot.
2.  Hold down "C" to boot from the CD.
3.  Install Ubuntu as usual, except:
•  In the partitioner, select Manually edit partition table
•  Delete /dev/sda3 and /dev/sda4 if they exist
•  Create a new ext3 partition for your root
•  Mount the newly created ext3 partition on '/'
•  On the last screen, click on the "Advanced" button and select instead /dev/sda in the drop-down list for installing GRUB

These are the directions i followed, except that in the kubuntu installation i could find no advanced button which allowed me to change the partition which installed GRUB.  Also, following these directions resulted in an error which stated that there was no room set aside for SWAP.  (Also, if it makes any difference, i'm installing the amd64 version.)

Problem Symptoms:
The install completed normally, but after reboot there was only the macintosh partition available  in Boot Camp, nor was it visible on my desktop.  I used Disk Utility, and the partition showed up as not being mounted.  Attempting to mount it resulted in an error, and attempting to verify the disk output:

> Verifying volume “disk0s3”
** /dev/disk0s3
Invalid BS_jmpBoot in boot block: 000000

So basically, the only thing I have accomplished is that I've reduced the size of my hard-drive by 32 GB.  :)

Any thoughts?

---

### Post by cyberdork33 on 2008-11-07
Ok, I know that you want kubuntu, and you can install that in the end, but i am going to mention using the _Ubuntu_ LiveCD because I know what tools are on there, and that they will work.

Install rEFIt... You need it (as instructed in the "no bootable devices" thread). In fact, you can install it to a USB device or make a CD. (Which you may need anyway) The instructions for this are on the rEFIt website.

Boot the Ubuntu LiveCD and start gparted (System > Admin > Partition Editor).
Select and delete any partition that is on the disk AFTER the OSX partition (HFS+). This should leave blank space to install Kubuntu. (Make sure to click "Apply" when you are done).

Shutdown and boot the kubuntu installer. In the installation process, you should be able to choose the option to "install to the largest continuous free space". Do this. Don't worry about directing GRUB to install to the partition instead of the MBR. Finish the install and shut down. Boot into the refit menu and sync the partition tables. after the tables are in sync, shutdown completely (not reboot) and start again... You should be able to choose to boot Kubuntu, if not, try shutting down completely one more time, and it should work.

If you STILL have issues, you will probably need to install grub manually to the root partition of your linux install as indicated at the bottom of the "no bootable devices" thread. and after that is should defintely work.

Good luck

I tried to outline the steps needed as well and contingency steps for the installation bug that has been ocurring in some people's machines.

---

### Post by fourth_stooge on 2008-11-08
thanks, CD.  worked like a champ.  i'm so new to linux that i foolishly expected it to work properly on the first try.  ;)

---

### Post by cyberdork33 on 2008-11-08
> **fourth_stooge said:**
> thanks, CD.  worked like a champ.  i'm so new to linux that i foolishly expected it to work properly on the first try.  ;)
can you detail what steps you had to take and mark this thread as solved from the thread tools menu at the top of the page?

---

### Post by fourth_stooge on 2008-11-08
> **cyberdork33 said:**
> can you detail what steps you had to take and mark this thread as solved from the thread tools menu at the top of the page?
my apologies, i was looking for how to mark it as solved.  The first portion of your suggestions worked without having to run any 'contingency plans.'  I simply burned rEFIt to a cd, used an iso of xubuntu i had already downloaded to delete the kubuntu partition, rebooted from the kubuntu live cd and reinstalled to the greatest free disk space.  Then i booted to the rEFIt disk, remapped the partitions and did a hard shut down.  Now i can choose to run Boot Camp whenever i want to use linux.   Thanks much.

---

