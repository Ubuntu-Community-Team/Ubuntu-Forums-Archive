---
title: "Help!Can not install xubuntu in my computer!"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by eqq2002 on 2008-01-02
I have a computer which has WINXP installed.
C: => winxp
D: => program files
E: => blank
F: => Documents

Now, I format E as fat32,and try to install xubuntu inside.
when I see partition, the disk is something like below:
 dev/hda
   dev/hda1 ntfs     [winxp]                 16G
   dev/hda2 fat32   [program files]     20G
   dev/hda3 fat32   [blank]                  20G
   dev/hda4 fat32   [Documents]         16G

so I partition the disk like the following:
 dev/hda
   dev/hda1 ntfs     [winxp]
   dev/hda2 fat32   [program files]
   dev/hda5 swap                                1024M
   dev/hda6 ext3    /                            19G
   dev/hda4 fat32   [Documents]

Before the seventh step,
I click [Advance], and choose to install grub in (hd0,5)

After the installation is performed,
I did not restart computer at once.
I instead to insert a Usb disk,then 
#ctrl alt F1
#sudo -i
#modprobe usb-storage
#dmesg  (USB is sda1)
# mount -t msdos /dev/sda1 /mnt 
# dd if=/dev/hda6 of=/mnt/linux.lnx bs=512 count=1 

restart computer to  winxp
copy linux.lnx to c:\
cmd Edit c:\boot.ini
add line at end of file
c:\linux.lnx="Xubuntu" and save(have change boot.ini's attibute)

then restart computer

select Xubuntu, only show "grub>" 
can not root (hd0,5), 

start ubuntu by liveCD, can not root (hd0,5) and (hd0,4) under grub command
disk is something like following:
 dev/hda
   dev/hda1 ntfs     [winxp]                 16G
   dev/hda2 fat32   [program files]     20G
   dev/hda3 fat32   [blank]                  20G
   dev/hda4 fat32   [Documents]         16G

where my installed Xubunt?

I have installed it at least 7 times!!!

Why?

---

### Post by luisromangz on 2008-01-02
I would let Grub, and not Windows, manage the boot, by installing Grub in the disk's MBR. I don't think that installing GRUB in a partition should work at all, but I may be wrong.

---

### Post by SOULRiDER on 2008-01-02
> **luisromangz said:**
> I would let Grub, and not Windows, manage the boot, by installing Grub in the disk's MBR. I don't think that installing GRUB in a partition should work at all, but I may be wrong.

I agree, use GRUB as a bootloader, not the windows one, you'll save yourself a lot of trouble. Remember the installed auto detects windows so you will be able to boot into it with GRUB.

---

### Post by LowSky on 2008-01-02
I would use grub and change to boot order to boot windows first, xubuntu second. And let grub install itsself, dont use the advanced feature. Mainly because your trying to install it to the wrong (if your chart is right it should be hd(0,2). Remember that fdisk mounts point are differnet from hd mount point. fdisk starts at 1, while the hard drive starts at 0. So if you Xubuntu is installed on the third partition on the first hard drive is should read hd(0,2)

---

### Post by eqq2002 on 2008-01-02
Hey,
In My first installation, I install grub by default setting. 
But it seems not work.
I may try it again.
During step 4  in installation( maybe i am wrong), LiveCD didn't detect windows account, so I think LiveCD didn't detect winxp yet. 

People  suggest me to use ntloader [winxp] to guid xubuntu,because I install AutoCAD in WINXP, so winXP may be reinstall [often ,winxp is not stable ], it will cover MBR automatically.So backup menu.lst and dd linux.lnx is better choice.
And My machine is lenveno, winxp has preinstalled inside with Ghost, someone's xp has collapsed when they install grub to MBR.

---

### Post by Ub1476 on 2008-01-02
It should work if you do not format the 20GB free space. Upon installation just select "use largest free space available". It will create swap, grub and ext3 automatically then. Always work fine for me (out of about 5 computers).

---

### Post by ukripper on 2008-01-02
> **eqq2002 said:**
> Hey,
someone's xp has collapsed when they install grub to MBR.

That is highly unlikely as grub is pretty smart bootloader it won't dump MBR unless you force it to while partiioning. If you are not sure what you are doing then  just select guided installation while installing xubuntu.

---

### Post by eqq2002 on 2008-01-02
> **Ub1476 said:**
> It should work if you do not format the 20GB free space. Upon installation just select "use largest free space available". It will create swap, grub and ext3 automatically then. Always work fine for me (out of about 5 computers).

I have never seen this screen before.Only two choices,use Whole IDE/manually.
You may be right.
But ext3 can not manager so big space?I keep my doubt.

---

### Post by eqq2002 on 2008-01-02
> **ukripper said:**
> That is highly unlikely as grub is pretty smart bootloader it won't dump MBR unless you force it to while partiioning. If you are not sure what you are doing then  just select guided installation while installing xubuntu.


I remember the default choice is "(hd0)", does that mean MBR or hda1?
or "MBR is inside hda1"?

---

### Post by jken146 on 2008-01-02
Your partitioning scheme is absolutely fine, but you should install GRUB to (hd0,0) -- this is hda1 in Linux or C:\ in Windows.  In other words, let GRUB install where it wants to.  If things go awry, it isn't hard to remove GRUB and restore the windows bootloader.

If you're still having trouble booting into either OS after installing like this, post the contents of /boot/grub/menu.lst please.

---

### Post by eqq2002 on 2008-01-02
Fine. I'll post the result after I try hda1.

---

