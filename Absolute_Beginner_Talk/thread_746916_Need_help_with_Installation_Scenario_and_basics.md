---
title: "Need help with Installation Scenario and basics"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Giving it a Try on 2008-04-06
I hava an old laptop whos CD drive doesn't work and USB is dead.

I want to install Ubuntu so this is what I'm trying to do.

I have partitioned the 5GB drive with TomsRtBt in the following manner?
Device            Boot            Start            End              Blocks              Id               System
/dev/hda1      *                     1               510              4096543          83              Linux
/dev/hda2                         511               527              136552            82              Linux swap
/dev/hda3      *                  528               730              1630597          83              Linux

I have formatted with
mke2fs /dev/hda1
mke2fs /dev/hda3 

I created a GRUB boot disk with RawWrite and a grubbootimage.img

Since I have no CD and no USB on this old Compaq Armada 1573DM, I thought well I can just remove the drive and connect it externally to another computer (Windows) and copy the Ubuntu ISO to one of the partitions to on the drive.
Now you might think how's this possible in Windows. I'm using a program called Ext2 IFS to do this. So I have the iso on the /dev/hda3 

How can I mount this for installation?
The problem is when booting the grub boot disk is weird (I'm new to this). I get a menu that is not very intuitive. Is there a preferable GRUB image to use (I don't have a Ubuntu instillation). Are there screen shot for the GRUB loader I can follow?

Any newbie help is appreciated.

thanks

---

### Post by zvacet on 2008-04-06
Try [this.](http://ubuntuforums.org/showthread.php?t=666267&highlight=iso)

---

### Post by Giving it a Try on 2008-04-06
Thanks for the link. It will come in handy, but my problem right now is booting GRUB. I can't seem toget to any kind of command prompt.

I really new at the bootloader stuff. What I need is a GRUB boot image to create a boot floppy. I only have windows.

---

### Post by zvacet on 2008-04-06
[Here](https://help.ubuntu.com/community/Installation/WithFloppies)

---

### Post by Giving it a Try on 2008-04-06
I'm at my wits end...

Any way, I got a copy of Gujin on a floppy to boot, but it can't boot the iso file on /dev/hda3

---

