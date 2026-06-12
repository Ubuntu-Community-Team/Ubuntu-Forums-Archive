---
title: "[SOLVED] Installation on slave hard disk"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by agerfe on 2007-11-09
Can I install Ubuntu on a slave hard disk?
I have two 250GB hard disks. The first one has three partitions with Windows occupying most of the first partition (C:/). The other two partitions are loaded with stuff. 
I'm hesitant to install Ubuntu on this hard disk because of the insufficient space as well as the fact that it is already partitioned in three.
Is is necessary to install Ubuntu on the master hard disk? The one were Windows is installed?
If the answer is yes, do I have to install it on the first partition, along side with Windows, or can I install it on a different partition?
Can I instead install Ubuntu on my slave hard disk? I'd prefer this because it would keep both operating systems separated from each other.
By the way, I will be installing Ubuntu Studio.
I'd appreciate any help.

agerfe

---

### Post by SkyNet2029 on 2007-11-09
No, you don't need to install ubuntu to the primary disk, as you can specify during the installation as to the exact device you want to install to. Just be very careful when you do choose the partition for installation, making sure you are specifying the correct device..

---

### Post by bulldog on 2007-11-09
> **agerfe said:**
> Can I install Ubuntu on a slave hard disk?
I have two 250GB hard disks. The first one has three partitions with Windows occupying most of the first partition (C:/). The other two partitions are loaded with stuff. 
I'm hesitant to install Ubuntu on this hard disk because of the insufficient space as well as the fact that it is already partitioned in three.
Is is necessary to install Ubuntu on the master hard disk? The one were Windows is installed?
If the answer is yes, do I have to install it on the first partition, along side with Windows, or can I install it on a different partition?
Can I instead install Ubuntu on my slave hard disk? I'd prefer this because it would keep both operating systems separated from each other.
By the way, I will be installing Ubuntu Studio.
I'd appreciate any help.

agerfe

Be a ware that grub will be installed on the first hdd,in your case the windows hdd.
This isn't a problem till you reinstall windows,which will over write your grub.
No problem if you know how to reinstall grub,but it could be a pain if you don't.

If your disks are both sata hdd's,you can simply change the bootorder in your BIOS.
If you have two sata hdd's let me know and I give you the best way to make a dual boot system.

---

### Post by agerfe on 2007-11-10
Thank you both, guys!
Yes, Bulldog, both are SATA hdd's. By dual boot system you mean I will be able to boot from either? That would be great! Please post those instructions as soon as you can. I'd appreciate it very much!
Thanks again!

agerfe

---

### Post by bulldog on 2007-11-10
Sata hdd's are both master the only difference is which one is to set to boot from.
I need you to go to the BIOS and set as first boot device the cd-rom **but set the slave hdd as first hdd to boot from** this are two different options in the BIOS.
Have a look around there it should be there if your motherboard is a native sata and you're not using a PCI sata card.

When done install ubuntu on the hdd you have set to boot from the 'formerly slave' that is it will be called sda and the windows hdd should be sdb.
Look carefull and in case of doubt use  the live cd and have a quick look with gparted.
It's possible that you have to switch your sata cables from place on the mobo,so that the 'slave' is on port one and the windows is on port two,in most cases this makes no difference but only to be sure.
We are only doing this to make no mistakes where grub will be installed,if you are confident enough with your system and know the difference from sda and sdb by their partitions,you can skip this,because you recognice the right hdd when you see it.
In case of a mistake there's no problem either,grub can be reinstalled very easy,and with your windows install cd,you can just as easy reinstall the windows loader.

Okay,when you came this far and know which hdd is the right one boot into the live cd and fire up gparted partitioner.
Choose the correct hdd for partitioning.
You should create one partition 10GB set it to format ext3 which will be used as / partition when we are going to install [make a note how the parttion is called]
Then create a partition 2GB for the swap and format it as swap.
If you have space left create a /home you can decide how big this will be,this one will be used for all your personal settings downloads and what not.
To apply this changes to your hdd,it must be umounted and gparted will tell you so,do it and apply the changes.
Make a note how all partitions on this disk are called so there should be no mistake when we install.

Now go back to the desktop and hit the install button.
Follow the steps till you come to the partition part,**choose manual partitioning** this will open a page with all your hdd's and partitions.
Choose the correct hdd by looking at the partitions,if found,choose the 10GB partition by selecting it and choose next,mount this as / ,set the bootflag enable and format ext3.
Then choose the 2GB partition,mount as swap format as swap
Then choose the partition you created for home,and mount it as /home set it this time to format ext3,in the case of a reinstall **never format this one again** because all your personal stuff will be on it.
Only when you don't want linux anymore you can delete it ofcourse.
Proceed with the install,in the end will grub be installed,it will look for other OS's and will make an entry for it in the menu.lst,so windows should be found and if we set things right it will be installed on the right hdd,and if not we can correct it.

Reboot when asked to,remove the cd and you can boot in ubuntu **not in windows,though** because we have to edit the menu.lst a little.
This is because windows likes to be on the first hdd and it isn't :) [you can boot into windows by changing the hdd's in BIOS so you boot from the windows hdd] but we are not going to do that.
When you boot into ubuntu and come to the desktop I need you to perform some commands in the terminal [ALT+F2 and in the box type gnome-terminal].
In the terminal copy/paste this command```
sudo fdisk -l
``` and post the output on the forum.
Now I can see what you have to change in the menu.lst to make windows boot from grub.

Well long story short this is about it.
Ofcourse you can have troubles with the graphics ore what not but basically,if you have a good copy of ubuntu,this shouldn't be to difficult.
I myself prefer to install with the alternate cd which has no graphic interface [live cd] this will install in about 20 minutes.

The big advantaged of this is,you can always boot your windows by switching the boot device in the BIOS.
And you can reinstall whitout loosing your personal stuff and preferences,and if you want,you can install more copy's of linux,the only thing you have to do is make about 10GB free space and create a / partition,you can use the same swap and /home.
The only thing you must be aware of,if you install more than one copy,with different preferences,**choose another logon and password for it** this will created a separate folder in your /home so things are not getting mixed up.

If you have any question before you start,just ask,I did this so many times,I can easily overlook things :)
Or if you have problems after the install,I will do my best to help you to solve them.

Good Luck

---

### Post by gary0 on 2007-11-10
I dual boot from 2 hard disks. This is how I did it...

Plug in first hd and make it master. Install windows. Unplug this drive and plug in second disk - make this master. Install Linux. Make this drive slave, and plug in the first hd and make it master. Now you have two disks installed (windows being primary master and linux being primary slave). Boot the computer, hit (in my case F11) at boot up to select your boot device, or just leave it and it will boot windows. There you go.

You can of course make the linux drive your primary and windows slave. 
Doing it like this doesn't mess with your windows mbr. So if you need to redo windows at any point in the future, you can just go ahead and do it knowing you linux installation will start perfectly well next time you boot it with out having to edit grub.lst. If you need to redo linux, unplug the windows disk first! You can still share ntfs drives and partitions using NTFS-3G using this method to boot.

Hope this helps,
Gary.

---

### Post by bulldog on 2007-11-10
A lot of 'plugging' there :)

Problem is your windows partitions aren't in the fstab,you'll have to put them there yourself.
Ofcourse you can mount and umount them with a terminal,but that's a pain in the *** everytime.
 
I'm not going to discuss what's 'the best way' of doing things.
I do this for several years now,and I know it works like a charme,booting from GRUB,choose the OS you want to boot and done,everything is auto mounted and ready to go.
Reinstalling windows is just as easy as in your way,except no unplugging,the same goes for linux.
No pushing buttons to choose the hdd,just plain grub and choose the OS,you can set in GRUB which OS you want to boot by default,the standard default is ubuntu,but by changing one tiny thing in menu.lst,it's set to another.

---

### Post by agerfe on 2007-11-10
Thank you so much Bulldog!
I'll be busy for a few days so I don't know when I'll have the time to do it but as soon as I do I'll post the terminal output and let you know.
I must confess I don't know much about installing an OS or partitioning hdd's but I think your instructions are pretty clear and I'm willing to try them.
I once studied Computer Systems Engineering (oriented to management information systems........ no hardware stuff, and not much software either,...... mainly logic and algorithms), but that was a long time ago - when floppy disks were still around! - and I really never liked the career. Now I'm a musician and frankly I have forgotten almost everything. :lolflag:
However I think I have a clear idea of what you are referring to in your instructions. 
So, maybe all those years of studying Systems Engineering weren't for nothing after all! We'll see that!
Just one more thing. At the end, when I turn on the computer, GRUB will load and ask me which OS I want to boot, right? No need to enter the BIOS unless I want to change the default, correct?
Thanks again for the help!

agerfe
P.D.: thank you too Gary. I'll try Bulldog's solution but any bit of information helps! :)

---

### Post by bulldog on 2007-11-10
Grub will give you a list with OS's,mainly three for ubuntu and one for windows.
If you do notthing it will boot ubuntu by default,the first entry.
The second entry is for recovery mode if things must be repaired.
The third is to do a memtest for the RAM,shouldn't need this one often though.
The fourth is your windows,**which will not boot** you need to add some lines in your menu.lst.
I'll give you an example how it should look,but to be totally sure,I need the output of the fdisk command.
```

### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

First make a safety copy of the menu.lst [make always a safety copy when you alter system files]
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
Next command is to edit the menu.lst,```
gksu gedit /boot/grub/menu.lst
```
Save it and when you reboot windows should work.

---

### Post by gary0 on 2007-11-12
Bulldog:
Problem is your windows partitions aren't in the fstab,you'll have to put them there yourself.
Ofcourse you can mount and umount them with a terminal,but that's a pain in the *** everytime

Not true... NTFS-3G and NTFS-3G config will find your newly plugged in windows disk and mount it for you. I use this method all the time and it works a treat. Keeps both your O/Ss completely separate from each other, so it is just a case of unplugging the windows disk to reinstall linux, or the other way round to reinstall windows. This way, if windows screws up, you can still just switch on and boot linux as linux hasn't been added to the windows mbr.

Each to their own eh?

Gary.

---

### Post by agerfe on 2007-11-29
Hey bulldog! Finally, after two weeks of hard work I have a free weekend and will be able to install ubuntu studio.

I was wondering if you'll be available this weekend to help me with the configuration of the GRUB, as you kindly offered to do.

One more thing. The hard disk on which I'll be installing ubuntu is relatively new and because I never used it I discovered this morning it had no format. So I did two things: first I created two 125GB partitions. And second: I formatted the second partition as I will be storing windows related files in there. The first partition I left it without format. Do I have to format this partition with Windows? Mi guess is: no...... but you have the last word.

Hope you can be able to help me this weekend.

Sorry for keeping you waiting!

---

### Post by agerfe on 2007-12-09
I followed Bulldog's instructions (long post) and was able to do the job correctly.

Thank you Bulldog!

There was no need to edit menu.lst. The installer was able to locate my Windows XP even though it's on a separate HDD and generated a proper entry. I'm able to boot Windows XP without any problems!

---

