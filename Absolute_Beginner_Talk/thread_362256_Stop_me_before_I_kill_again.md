---
title: "Stop me before I kill again"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by roodscreen on 2007-02-15
I am facing the fifth install (the third today) sigh. I have been trying for a week to resolve my resolution problem. It is stuck in 640x480.

I have searched the forums and attempted every fix that fit my situation. I have gone to the Ubuntu docs page, searched offline, etc.

I have installed 915resolution

run 915resolution -l

changed the /etc/default/915resolution file

I have also run the various autoconfig routines.

Altered the xconf. file

(I am not being thorough in explaining my exploits, but it is all a blur). 

I know that the screen resolution supports 1024x768 since this is what how it ran in Windows and I was able to get it to run in Ubuntu under a commercial program from Userful (however, it posted a black nag screen every two minutes until I registered - yet no one at Userful can explain to me how to register the program - Oi)

The last three times I have changed the 915resolution file to support 1024x768 with a 16bit/pixel color depth, the system tells me, upon reboot, that the configuration is wrong and that I must correct it before I can run Ubuntu again. Since I am not able figure out how to run 'gedit' from the command line, I have had to reinstall Ubuntu.

I am frustrated out of my mind. I have researched, read, tried, and failed to get Ubuntu correctly configured. Never does the screen resolution offer any other than 640x480. Last night I spent 4 hrs on several different solutions and after two reinstalls, I put it aside.

Any suggestions? I have one more wack in reinstall before I give up. I am just so frustrated by the entire ordeal.

---

### Post by lukew on 2007-02-15
Hi,

If you:

[HTML]sudo dpkg-reconfigure xserver-xorg[/HTML]

You can add resolutions into the list.

I would not bother reinstalling ubuntu; you can change everything with regards to the graphics with a live installation.

Luke

---

### Post by Tomosaur on 2007-02-15
Please post the /etc/X11/xorg.conf file.

I assume you're using an integrated graphics chip/card, which is why you're trying 915resolution? Your system specs would also be nice, but they're probably not an issue (except for any details you can give about graphics card/chip.)

---

### Post by roodscreen on 2007-02-15
Luke, thanks for the quick reply. I have attempted to figure out how to change the files from the Live CD. However, I cannot figure out how to get to the 'non-live cd files' when I boot from the CD. The user is set to the user ubuntu@ubuntu. How do I get from there to michael-desktop?

---

### Post by Tomosaur on 2007-02-15
short answer: You need to mount your hard drive.

Long answer: Do this command in the terminal:
```

sudo fdisk -l

```
You'll see something like this:
```

/dev/hda1               1         789     5964808+  1c  Hidden W95 FAT32 (LBA)
/dev/hda2             790        4950    31457160   83  Linux
/dev/hda3            4951        5019      521640   82  Linux swap / Solaris
/dev/hda4   *        5020       21174   122131800    7  HPFS/NTFS

```

If I wanted to mount my Linux drive, I'd do the following:
```

mkdir ~/my_hd
sudo mount /dev/hda2 ~/my_hd

```

Then you can access your hard drive through the newly created my_hd folder.

---

### Post by roodscreen on 2007-02-15
Again, thanks for the quick reply. When I went to mount the drive to access the files, I did the following and got the result following result:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19075   153219906   83  Linux
/dev/hda2           19076       19452     3028252+   5  Extended
/dev/hda5           19076       19452     3028221   82  Linux swap / Solarisubuntu@ubuntu :~$ mkdir ~/my_hd
ubuntu@ubuntu:~$ sudo mount /dev/hda2 ~/my_hd
mount: you must specify the filesystem type
ubuntu@ubuntu:~$

Your instructions were very clear, what in the world did I do wrong?

---

### Post by roodscreen on 2007-02-15
> **Tomosaur said:**
> Please post the /etc/X11/xorg.conf file.

I assume you're using an integrated graphics chip/card, which is why you're trying 915resolution? Your system specs would also be nice, but they're probably not an issue (except for any details you can give about graphics card/chip.)


I am having trouble getting into the xorg.conf file because I need to figure out how to mount the drive. 

I went back to a prior post and saw that I had posted this

> I have the Intel 82865G chipset with the i810 driver

So, yes, I am using the 915resolution because of using the Intel 865G chipset.

 If you need more info on the xorg.conf, I will post it once I can get back into my directories.

Thanks for your help.

---

### Post by meborc on 2007-02-15
you can get to your xorg.conf file through windows (if you are dual-booting)

you need this [http://www.fs-driver.org/](http://www.fs-driver.org/) to see your linux filesystems in windows...

hope it helped!

---

### Post by Tomosaur on 2007-02-15
you got the filesystem error because you did hda2. Try using hda1 and check if that works:
```

sudo mount /dev/hda1 ~/my_hd

```

---

