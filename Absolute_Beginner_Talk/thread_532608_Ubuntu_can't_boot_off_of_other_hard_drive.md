---
title: "Ubuntu can't boot off of other hard drive"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by b.mann on 2007-08-22
Here's my problem. I had installed Ubuntu on one of my hard drives (60GB) while dual booting Vista off of the same hard drive. Somehow, I messed up the boot settings of Vista, and could not boot either OS from that hard drive. Now I have XP installed onto my other hard drive (160GB), yet XP doesn't boot off of this one, meaning my 60GB still has to be set as the master drive. The 60GB also cannot be reformatted, yet I can still see the 25GB Windows partition, and I believe the other 25GB Linux Partition is still there. Is there a way for me to be able to format the old hard drive, get XP to boot off of the newer one, and still be ablt to dual boot?

---

### Post by logos34 on 2007-08-22
I'd first try installing grub to the MBR of the 60GB drive and hope that allows you to get into ubuntu.  Then you can go from there and add entries to your grub config files to boot the other OS's. 

Boot from the Feisty live cd, load the desktop and click on your ubuntu root partition (Places>Home folder).  It should mount as 'disk'.  Go inside to the /boot/grub folder.

Copy and post the menu.lst file. 

Run the following command in a terminal and and post it too:

sudo fdisk -l

---

### Post by b.mann on 2007-08-23
> **logos34 said:**
> I'd first try installing grub to the MBR of the 60GB drive and hope that allows you to get into ubuntu.  Then you can go from there and add entries to your grub config files to boot the other OS's. 

Boot from the Feisty live cd, load the desktop and click on your ubuntu root partition (Places>Home folder).  It should mount as 'disk'.  Go inside to the /boot/grub folder.

Copy and post the menu.lst file. 

Run the following command in a terminal and and post it too:

sudo fdisk -l

I haven't fully installed it back onto the hard drive it was previously on, but when I did run the sudo fdisk -l command, this is what I got

```
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3295    26467056   42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3296        7297    32145592+  42  SFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6935    52428568+   7  HPFS/NTFS
/dev/sdb2            6936       20673   103859280    f  W95 Ext'd (LBA)
/dev/sdb5            6936       13891    52587328+   7  HPFS/NTFS
/dev/sdb6           13892       20673    51271888+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 


```

The only other thing that I don't understand about using Ubuntu is with my wireless drivers. If Ubuntu comes up with available wireless connections, does that mean that my wireless adapter is recognized, or do I still need the specific drivers?

---

### Post by mrfelker on 2007-08-23
There are several possibilites.  Using a boot loader program like Terabyteunlimited BooITNG you could setup a primary partition on drive 1 using Vista.  Before hand back your data of course.  Then you can install Windows XP on the drive of your choice.  Vista will pickup the XP OS BUT it will use the Vista Bootloader and XP will be called "previous version of windows".  What I would do is use Vista to remove the drive letter for the XP partition and then when XP is on remove the drive letter for Vista (Administrative Tools _> Computer Management -> Disk management.  This is to avoid data corruption which is certainly possible using two windows OS's.

Or like others have posted, you can just install whatever Windows you want and after that install Ubuntu.  I would think of using the alternate install image - but not if you don't want a text only install.  Windows will write to the MBR - Ubuntu will fix that and install GRUB in MBR and then you can use the Vista Bootloader (which it will pickup) instead of a direct boot to Vista or XP.

Multbooting is fairly difficult with several operating systems - but after awhile (took me 10 years) it gets easier.  

The main rule is always Windows (actually you should install the oldest - XP _ first and then Vista) and then put on Ubuntu and use Synaptic to search for "ntfs" and you'll find programs that will allow you to rad AND write to Windows.  This means, for example, that you could use OpenOffice on Ubuntu - already comes with it and open documents on the Windows partition(s) to edit as you choose.

Goog luck.

---

### Post by wolfen69 on 2007-08-23
to answer your wireless question, yes, it is recognized.

---

### Post by b.mann on 2007-08-23
> **mrfelker said:**
> There are several possibilites.  Using a boot loader program like Terabyteunlimited BooITNG you could setup a primary partition on drive 1 using Vista.  Before hand back your data of course.  Then you can install Windows XP on the drive of your choice.  Vista will pickup the XP OS BUT it will use the Vista Bootloader and XP will be called "previous version of windows".  What I would do is use Vista to remove the drive letter for the XP partition and then when XP is on remove the drive letter for Vista (Administrative Tools _> Computer Management -> Disk management.  This is to avoid data corruption which is certainly possible using two windows OS's.

Or like others have posted, you can just install whatever Windows you want and after that install Ubuntu.  I would think of using the alternate install image - but not if you don't want a text only install.  Windows will write to the MBR - Ubuntu will fix that and install GRUB in MBR and then you can use the Vista Bootloader (which it will pickup) instead of a direct boot to Vista or XP.

Multbooting is fairly difficult with several operating systems - but after awhile (took me 10 years) it gets easier.  

The main rule is always Windows (actually you should install the oldest - XP _ first and then Vista) and then put on Ubuntu and use Synaptic to search for "ntfs" and you'll find programs that will allow you to rad AND write to Windows.  This means, for example, that you could use OpenOffice on Ubuntu - already comes with it and open documents on the Windows partition(s) to edit as you choose.

Goog luck.

Thanks, but I dont want Vista, and somehow i think its stuck on the older hard drive because i messed up those boot settings. But for now I give up on using Ubuntu, I've been trying to get my wireless setup for months now with no luck.

---

