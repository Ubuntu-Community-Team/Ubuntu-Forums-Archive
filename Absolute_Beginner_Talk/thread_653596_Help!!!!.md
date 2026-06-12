---
title: "Help!!!!"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Strasher on 2007-12-30
Hello everyone!
I have a very important matter regarding my acer laptop. I installed Ubuntu  on it I got the install right. So I turned off the live CD and made sure windows worked. BUT IT DOESN'T!!!
It booted me to the recovery part of my acer partions. So i  went into a HUGE panic and quickly delted the partion and tried booting windows again. But now I have the "GRUB" boot loader insted of just the normal MBR one. I get Error 22.
How to I get rid of the grub boot loader?! I don't have a windows CD. Windows came pre-installed on it. Please help! :([-o<

---

### Post by meierfra on 2007-12-30
To fix your problems you will have edit the file  "menu.lst"
and reinstall Grub. I can give you detailed instruction but I need some information:

Boot from the Ubuntu LiveCD.

Go to Places->Computer and double click the Ubuntu partition. (This mounts your Ubuntu partition.)

Post the output of 

```
sudo fdisk -l
```

and

```
cat /media/disk/boot/grub/menu.lst
```

---

### Post by meierfra on 2007-12-30
Actually if you just want to fix the MBR click on FiXMBR in my signature. The third method can be done from the Ubuntu Live CD.

With the information from my first post. I can (hopefully) show you how to boot into Ubuntu and Windows.

---

### Post by maniac_X on 2007-12-30
first thing........DON"T PANIC!!!!  Keep a cool head and don't delete anything else yet.

That being said, I had a similar problem some time ago. There are differences though. I don't have a laptop with a diagnostic partition on it like you do. I can get you the .iso for a Win boot disk though(actually a Win98 boot disk on CD).  It might come in handy for you. Here's my old post for reference, the link to the .iso is still good it seems:
[http://ubuntuforums.org/showthread.php?p=3611312#post3611312](http://ubuntuforums.org/showthread.php?p=3611312#post3611312)

good luck and check back here, I'm sure someone with similar experience as your "laptop situation" will post back.

lol,  seems I just type way to slow for some of these linux pros (points at posts above :P )

---

### Post by Strasher on 2007-12-30
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638        4461    30716280    c  W95 FAT32 (LBA)
/dev/sda3            5152        9729    36772785    c  W95 FAT32 (LBA)

```
theres the sudo fdisk -l 
```
cat: /media/disk/boot/grub/menu.lst: No such file or directory

```
:confused:

---

### Post by Paulmd on 2007-12-30
> **Strasher said:**
> Hello everyone!
I have a very important matter regarding my acer laptop. I installed Ubuntu  on it I got the install right. So I turned off the live CD and made sure windows worked. BUT IT DOESN'T!!!
It booted me to the recovery part of my acer partions. So i  went into a HUGE panic and quickly delted the partion and tried booting windows again. But now I have the "GRUB" boot loader insted of just the normal MBR one. I get Error 22.
How to I get rid of the grub boot loader?! I don't have a windows CD. Windows came pre-installed on it. Please help! :([-o<


First: stop panicking.

second: windows, and your files are probably recoverable, but it's tricky. You must be careful not to take steps that can make the situation worse.


third:

If you have a spare hard drive of equal or greater capacity then your laptop's, i'd make a clone of it. So if you screw up the recovery, you have a backup copy.

fourth:

determine what precisely is wrong, Did you nuke the Window's partition? 

If you didn't destroy the Windows partition, you should be able to read it, and pull any personal files.



If you feel you are out of your depth, seek out a repair shop and give them a set of instructions regarding what you want done. Indicate whether you want them to recover your documents, before re-installing windows. You could even ask them to set up a dual boot for you.

---

### Post by meierfra on 2007-12-30
I misunderstood.  I thought you had deleted the recovery partition. Stupid me. You deleted Ubuntu. Well you could fix  Grub by reinstalling Ubuntu. But lets fix your MBR first
and make sure that Windows is o.k:


 Boot  from the Ubuntu Live CD and make sure you have a working internet connection.

Step I) Enable the "universe" repositories. 

Go to Systems-> Adminstration->Software Sources"

Click on the Box next to "Community-maintained Open Source Software (universe)

Click on Close (twice)

Step II)   Install the package "ms-sys"  ([Info on ms.sys]("http://ms-sys.sourceforge.net/")
 In a terminal

```

sudo apt-get update
sudo apt-get install ms-sys

```

Step III) Use "ms-sys" to installed a windows type boot-loader to the MBR:

```
sudo ms-sys -m /dev/sda

```

---

### Post by Strasher on 2007-12-30
THANK YOU!!! 
THANK YOU SO MUCH!!
It worked! windows now boots, all the files are in good order! You fixxed my com! THANK YOU SO MUCH!
I'll be staying away from linux for a long time tho..

---

### Post by meierfra on 2007-12-30
> THANK YOU SO MUCH!!

You are  welcome.

Don't hesitate to install Ubuntu again. And if  you get unlucky again, and you are not  able to boot into Windows, just come back to the forums and you will find somebody who can help you.

---

### Post by Paulmd on 2007-12-30
> **meierfra said:**
> You are  welcome.

Don't hesitate to install Ubuntu again. And if  you get unlucky again, and you are not  able to boot into Windows, just come back to the forums and you will find somebody who can help you.

Whether or not you decide to go with linux in the future, this experience demonstrates the importance of making a backup. Hard drives can and do fail regularly, for unsoftware related caues, and there are plenty of situations that can make an operating system unusable that are software related, where restoring form backup is far easier to do than fixing the issue (some virii are nasty).

In Windows, there are many good programs to backup either just a few important files, or the whole OS. 

Since you have a computer that did not come with the OS CDs, I would recommend a tool that does cloning, Such as Ghost, or Acronis True Image. There are others. And even gparted, the linux partition editor is good for that, it has a live-cd version.

---

