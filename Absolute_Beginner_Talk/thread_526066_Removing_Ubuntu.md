---
title: "Removing Ubuntu"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by skie22 on 2007-08-15
I installed ubuntu on a seperate hd on my lappy and now i figure its taking waay too much space, so i need to uninstall it and configure the harddrive to work with my primary operating system - vista. Any suggestions on how to do this? Since windows doesn't recognize the hd i cant use dos to format it, and im not familiar enough with the ubuntu console, help!?

---

### Post by Arthur Archnix on 2007-08-15
```
sudo apt-get install gparted
```

Then in your system, administration menu, you'll see gparted. You can use that to resize your ubuntu install, (hint: Vista is going to be NTFS or something, and Ubuntu will be Ext3). You can use this to resize ubuntu. Then reboot into Vista find your disk manager (I think it's right click on my computer and then disk management) and resize Vista to use the free space.

Any questions, post a screenshot of your gparted, or post the output of 
```
sudo fdisk -l
```
and someone will be able to help you.

---

### Post by ugm6hr on 2007-08-15
> **skie22 said:**
> I installed ubuntu on a seperate hd on my lappy and now i figure its taking waay too much space, so i need to uninstall it and configure the harddrive to work with my primary operating system - vista. Any suggestions on how to do this? Since windows doesn't recognize the hd i cant use dos to format it, and im not familiar enough with the ubuntu console, help!?

If you want to uninstall Ubuntu - first thing to do is to ensure Vista can boot.  Try this:
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

As for wiping Ubuntu - doesn't Vista even see the drive as unformatted?  If not - easiest way is to use the GParted LiveCD, and delete the partition and reformat from there:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Arthur Archnix on 2007-08-15
I'm sorry, I didn't read your post clearly enough. 

Reboot into Vista and use it's disk manager to delete the ubuntu  partition. BUT FIRST... read this thread, and follow Ted's instructions.

[HERE:]("http://ubuntuforums.org/showthread.php?t=463534&highlight=Ted+Nancy")

Once you've successfully booted into Vista without seeing Grub you can safely delete the Ubuntu partition and resize from within Vista.

---

### Post by ugm6hr on 2007-08-15
> **Arthur Archnix said:**
>  BUT FIRST... read this thread, and follow Ted's instructions.
[HERE:]("http://ubuntuforums.org/showthread.php?t=463534&highlight=Ted+Nancy")


EasyBCD will achieve the same thing, with additional options for future editing (in case you want to play with an alternative OS in the future again).

---

### Post by kwiwii on 2007-08-15
As others have said, make sure that you can boot Vista without Grub. 

And than just reformat the Drive.

You can make a livecd of GParted:
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by ubuntolover2000 on 2007-08-24
hi all

my problem is a peculiar one. i installed 7.04 ubuntu in my desktop which already had win xp prof.  about two months ago and was happy with it.  however, yesterday, after a sudden power cut, when i rebooted the computer, i found some error messages.

so next day i brought the ubuntu installation cd and reinstalled the the ubuntu. so it is running fine in my pc.  however i noticed that the old ubuntu installed is still in my computer.

so in effect i have two ubuntu installed in my pc-the old one is not functional and the new one is working fine.

my questions are:-
is the old non-functional version is eating up a portion of the hard disk? and

how to delete the old non-functional version of the ubuntu?

please help me.:confused:

ubuntolover

---

