---
title: "How to set up ubuntu with 2 hds"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by awec56a8 on 2007-09-23
hi newbie question here!
I have been a window user since 3.1, just give ubuntu a shot and loving it ever since. i dual boot with winxp in 1 hd and ubuntu in the other, and decided to rid of winxp. so here's my question:
1)how do i install the ubuntu os/program in 1 hd
2)my data in other 2 hd for instance(my docs in 2nd hd and pics and home video in 3rd hd)
i was told about using gparted. but how do i set it up and should i need to reinstall the os again, my docs and pics are save.

thank you guys for your suggestion and tips.
awec56a8):P

---

### Post by PmDematagoda on 2007-09-23
> **awec56a8 said:**
> hi newbie question here!
I have been a window user since 3.1, just give ubuntu a shot and loving it ever since. i dual boot with winxp in 1 hd and ubuntu in the other, and decided to rid of winxp. so here's my question:
1)how do i install the ubuntu os/program in 1 hd
2)my data in other 2 hd for instance(my docs in 2nd hd and pics and home video in 3rd hd)
i was told about using gparted. but how do i set it up and should i need to reinstall the os again, my docs and pics are save.

thank you guys for your suggestion and tips.
awec56a8):P

Now let me straighten it out a little.

You currently have XP and Ubuntu, XP in the first HDD and Ubuntu in the second one.

Now you want to uninstall XP and install Ubuntu in the place of XP and use your second hard drive for storage? If so then you will have to reinstall Ubuntu as you can't get it running just by copying all the system files to the other hard drive.

You don't need to use Gparted if you are having 2 hard drives and intend to use each for separate purposes.

---

### Post by awec56a8 on 2007-09-24
:confused:
hi thank you for your explanation, but i was more like how do i format my 2nd hd and move my home directory to my 2nd or even add a third hd as well.

thank you so much your time and effort.

regards,
awec56a8

---

### Post by aspen_dv on 2007-09-24
You can install Ubuntu, select one drive for OS (say hda). Once installation complete, you just format 2nd drive and mount it (hdb), modify /etc/fstab a little bit and make your 2nd drive data drive as you wish. 
Wait, you need to format and mount...here is a good link:
[http://www.idevelopment.info/data/Unix/Linux/LINUX_PartitioningandFormattingSecondHardDrive_ext3.shtml](http://www.idevelopment.info/data/Unix/Linux/LINUX_PartitioningandFormattingSecondHardDrive_ext3.shtml)

---

### Post by Shazaam on 2007-09-24
If I am reading your post right there is no need to reinstall. But, we need to know where grub is installed.
Once we know that it is simple. Unplug the Windows drive, change the hard drive jumpers/cables to reflect the new drive config, edit fstab to point to the new drive info (ie. hdb to hda etc), edit grub the same as fstab concerning the drives and you are off.
Later on you can plug the Windows drive back in, boot the livecd and partition it the way you want. But first find out where grub is installed (which drive mbr/partition).
Also, please post the output of fdisk -l here.

---

### Post by awec56a8 on 2007-09-25
:-P
hi guys thank you so much for your time to answer my question, and the link as well.

regards,

awec56a8

---

