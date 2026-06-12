---
title: "ready to give up -- nothing works"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by mikeb on 2007-07-20
I can't boot into Ubuntu. I reformatted my Windows partition and for reasons that I don't understand, Grub only sees an old version of Ubuntu and Windows (which no longer exists). I have tried to update Grub, I have downloaded and run Super Grub Disk, I have manually edited files and searched for a solution but nothing works. Even Super Grub disk finds my new installation of Ubuntu, but when I select it to boot, I get a "file not found" error!

If no one can tell me how to fix this problem, I'm afraid its back to Windows (yeech!).

---

### Post by AlexenderReez on 2007-07-20
if you have format windows and ubuntu...i suggest you to remove completely ubuntu and install windows first...then install ubuntu(incase you need windows for some reason next time)...you need to search for guide about installation,if you don't know...don't try and error......you didn't clarify your problem....please explain a little bit....

---

### Post by Kobalt on 2007-07-20
How is your HD set up? Do you want to install Ubuntu only on the whole HD? Do you use a dual-boot with windows? 
How about your hardware : is it an ATA, SATA or RAID drive?

If it's the most standard of choice (meaning a clean install of Ubuntu on a whole ATA/SATA drive) I 'd recommend you to completely blank the disk with [KillDisk]("http://www.killdisk.com") then try to install back Ubuntu using the AlternateCD.

---

### Post by ddrichardson on 2007-07-20
First how is your drive partitioned? 
Which drive is it? 
Where did you format the Windows partition from?
Post a copy of your /boot/grub/menu.lst

---

### Post by mikeb on 2007-07-20
OK, sorry if I was not specific enough. The machine has one HD with three partitions. I had Ubuntu 6.06 on one, Windows on another and Ubuntu 7.04 on the last. I reformatted Windows and use it for storing data. When I rebooted from Ubuntu 7.04, Grub loaded but only offered Ubuntu 6.06 and Windows (which had already been deleted). I tried to do update-grub, but nothing changed. Windows is already gone. Ubuntu 7.04 is on /dev/hda4 and Ubuntu 6.06 is on /dev/hda2

Here is menu.lst, but Super Grub disk has created a new file somewhere (I don't know the name of it) so it supercedes menu.lst

```


title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by Rocket2DMn on 2007-07-20
I'm no pro at GRUB stuff, but I don't see /dev/hda4 anywhere in that menu.list file.  You may have to add the correct line manually.

---

### Post by mikeb on 2007-07-20
> **Rocket2DMn said:**
> I'm no pro at GRUB stuff, but I don't see /dev/hda4 anywhere in that menu.list file.  You may have to add the correct line manually.

I'm not a pro either. The problem is 1. that I can't just add one line, I need to fill in a lot more information and I don't know where to get it. Secondly, when I used Super Grub disk it created a new file that the system now looks at to get the boot list and I don't know where that file is or what it is called or how to get rid of it!

Any help would be much appreciated!!!!

---

### Post by ddrichardson on 2007-07-20
At what point do you get the "File not found" error - post Grub?

Super Grub doesn't appear to create its own menu.lst rather to modify your current one. Thing is I'm not sure if its repairing the one on the installation that's booting.

Rocket2DMn is correct however as this menu.lst doesn't contain a reference to another partition.

Actually the lines are quite straight forward:

> title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

This is a good template, you just need to amend it for the correct values for partition, kernel and initrd.

---

### Post by asmoore82 on 2007-07-20
okay, we can rebuild him!! make him faster, stronger, but ...

The root (no pun intended) of the problem is this:

GRUB lives in the Master Boot Record of your hard drive, But the MBR is not big enough to hold all of GRUB's features and config so soon after the MBR portion of GRUB is initalized it calls up the bigger, better GRUB (called stage 2)  that lives in the /boot directory of your Linux installation, from there it reads the config file menu.lst and only then are you presented with the nice neat menu that holds the keys to your various OS's.

So, the issue is that you now have 2 separate stage 2's of GRUB on your system, one on /dev/hda2 and another on /dev/hda4 ...
1. which menu.lst did you post??
2. at this point we can't be sure which "stage 2" is being loaded, so do you feel confident that you can use ANY live linux disk and edit _BOTH_ of your stage 2 config files to do the same thing... so that it won't matter which one it loads: either will successfully load your Ubuntu 7??

:D on a side note it is entirely possible that you have been running the kernel from your Ubuntu 6 install while using your Ubuntu 7

---

### Post by adrian15 on 2007-07-20
> **mikeb said:**
> OK, sorry if I was not specific enough. The machine has one HD with three partitions. I had Ubuntu 6.06 on one, Windows on another and Ubuntu 7.04 on the last. I reformatted Windows and use it for storing data.

This is when you changed the partition numering scheme I suppose.
> **mikeb said:**
> 
When I rebooted from Ubuntu 7.04, Grub loaded but only offered Ubuntu 6.06 and Windows (which had already been deleted).

I tried to do update-grub, but nothing changed. Windows is already gone. Ubuntu 7.04 is on /dev/hda4 and Ubuntu 6.06 is on /dev/hda2

This is because update-grub only works with mountable partitions (I think. I am not very sure.)
> **mikeb said:**
> 
Here is menu.lst, but Super Grub disk has created a new file somewhere (I don't know the name of it) so it supercedes menu.lst

I think that you have used the Super Grub Disk -> Fix Boot of Linux option.
And that SGD has linked it to the U606 menu.lst instead of the U704 menu.lst.

If you use the last versions of Super Grub Disk ( 0.9598 ) and the Fix Boot of Linux option you should be able to select the stage1 from the U704 partition  so that SGD links your MBR to the U704 menu.lst. 

Previous versions restored grub from the first partition where stage1 was found instead of giving a choice to the user, this may be your cause.

If you still have problems you might try the "Linux -> Boot Linux directly" option to select one specific linux and initrd.

adrian15

P.S.: When you say "I have used Super Grub Disk" you have to say ** which option ** you have used.

---

### Post by mikeb on 2007-07-20
> **asmoore82 said:**
> okay, we can rebuild him!! make him faster, stronger, but ...

The root (no pun intended) of the problem is this:

GRUB lives in the Master Boot Record of your hard drive, But the MBR is not big enough to hold all of GRUB's features and config so soon after the MBR portion of GRUB is initalized it calls up the bigger, better GRUB (called stage 2)  that lives in the /boot directory of your Linux installation, from there it reads the config file menu.lst and only then are you presented with the nice neat menu that holds the keys to your various OS's.

So, the issue is that you now have 2 separate stage 2's of GRUB on your system, one on /dev/hda2 and another on /dev/hda4 ...
1. which menu.lst did you post??

It can only be the one from /dev/hda2
> 
2. at this point we can't be sure which "stage 2" is being loaded, so do you feel confident that you can use ANY live linux disk and edit _BOTH_ of your stage 2 config files to do the same thing... so that it won't matter which one it loads: either will successfully load your Ubuntu 7??

At this point, I've got almost nothing left to lose! I'll try anything. What do I have to do now?

> 
:D on a side note it is entirely possible that you have been running the kernel from your Ubuntu 6 install while using your Ubuntu 7

I strongly doubt that. I installed Ubuntu 7 and immediately started running it.

---

### Post by Rocket2DMn on 2007-07-20
Now you need to boot from the LiveCD so you can access the file(s) and modify them.
You will need to navigate to the correct menu.list file (on the correct hard drive partition) and add the capability to read the 7.04 partition.  You will base your template on the ones already in menu.list and you can actually browse the filesystem the *kernel* and *initrd* values (just look at tbe files).

---

### Post by mikeb on 2007-07-20
> **Rocket2DMn said:**
> Now you need to boot from the LiveCD so you can access the file(s) and modify them.
You will need to navigate to the correct menu.list file (on the correct hard drive partition) and add the capability to read the 7.04 partition.  You will base your template on the ones already in menu.list and you can actually browse the filesystem the *kernel* and *initrd* values (just look at tbe files).

OK, I just tried this, but I don't have permissions to save any of the files. I am booted off the Live CD. How can I get around that?

---

### Post by mikeb on 2007-07-20
> **adrian15 said:**
> 
I think that you have used the Super Grub Disk -> Fix Boot of Linux option.
And that SGD has linked it to the U606 menu.lst instead of the U704 menu.lst.

If you use the last versions of Super Grub Disk ( 0.9598 ) and the Fix Boot of Linux option you should be able to select the stage1 from the U704 partition  so that SGD links your MBR to the U704 menu.lst. 

I downloaded it today, so I assume it is the latest version.  I'm afraid I don't understand what you just said.

> 
If you still have problems you might try the "Linux -> Boot Linux directly" option to select one specific linux and initrd.

adrian15

P.S.: When you say "I have used Super Grub Disk" you have to say ** which option ** you have used.

I used the Linux option. It found the correct version of Ubuntu and said that it had succeeded in saving the Grub file. However, when I tried booted directly from Super Grub disk, that did not work either.

---

### Post by grishenko2000 on 2007-07-20
first mount one of the partitions /dev/hda2 or /dev/hda4
look around on the partition you should be able to tell which one its version 6.01 and which 7.04.
then edit the menu.lst file on each patition and change the title of the first entry so you can determine if you are booting from /dev/hda2 or /dev/hda4.

---

### Post by adrian15 on 2007-07-20
> **mikeb said:**
> I downloaded it today, so I assume it is the latest version.  I'm afraid I don't understand what you just said.



I used the Linux option. It found the correct version of Ubuntu and said that it had succeeded in saving the Grub file. However, when I tried booted directly from Super Grub disk, that did not work either.

I don't quite understand then what happens in your computer.

It's ok about the directly boot option not working.

If you choose "Linux -> Boot Linux" and try to boot one or another Ubuntu, do you get access to your Ubuntu 7.04 or not ?

adrian15

---

### Post by mikeb on 2007-07-20
> **grishenko2000 said:**
> first mount one of the partitions /dev/hda2 or /dev/hda4
look around on the partition you should be able to tell which one its version 6.01 and which 7.04.
then edit the menu.lst file on each patition and change the title of the first entry so you can determine if you are booting from /dev/hda2 or /dev/hda4.

OK, I've done that. The only question now is whether I can remove the Super Grub Disk settings and go back to the normal menu.lst

---

### Post by mikeb on 2007-07-20
> **adrian15 said:**
> I don't quite understand then what happens in your computer.

It's ok about the directly boot option not working.

If you choose "Linux -> Boot Linux" and try to boot one or another Ubuntu, do you get access to your Ubuntu 7.04 or not ?

adrian15

OK, that worked! Now the question is: I've edited the menu.lst files on both partitions, how do I disable the Super Grub Disk settings so that I can see if it can boot normally?

---

### Post by adrian15 on 2007-07-22
> **mikeb said:**
> OK, that worked! Now the question is: I've edited the menu.lst files on both partitions, how do I disable the Super Grub Disk settings so that I can see if it can boot normally?

Hemm, Super Grub Disk setting is a no sense thing. Super Grub Disk links to U606 menu.lst or to U704 menu.lst. Usually you should be able to use the Linux -> Fix Boot of Linux and choose the other partition in order to come back to normal settings.

As long as you say you only say one stage1 instead of two then you should do the following thing:

Boot the distro with Linux -> Boot Linux and from it run a shell as root and run:

grub-install /dev/sda

if your hard disk is sda of course.

adrian15

---

### Post by adrian15 on 2007-07-23
> **adrian15 said:**
> Hemm, Super Grub Disk setting is a no sense thing. Super Grub Disk links to U606 menu.lst or to U704 menu.lst. Usually you should be able to use the Linux -> Fix Boot of Linux and choose the other partition in order to come back to normal settings.

As long as you say you only say one stage1 instead of two then you should do the following thing:

Boot the distro with Linux -> Boot Linux and from it run a shell as root and run:

grub-install /dev/sda

if your hard disk is sda of course.

adrian15

Can you please make a test for me from a linux shell once booted your system run these commands:

$ sudo updatedb
$ locate stage1

Does locate find stage1 on /boot/grub  (CORRECT) or in /lib/grub (INCORRECT) ?

This result might explain a lot of things.

adrian15

---

