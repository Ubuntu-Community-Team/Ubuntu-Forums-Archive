---
title: "[SOLVED] Broken GRUB after modified partition"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Jacdeb6009 on 2008-03-27
Help... please...

I run Fiesty (7.04) together with Win XP in a dual boot setup.  Everything has been working fine for about two weeks and I am getting quite comfortable with Linux and less so with Windows :)

There was about 40Gb on my hard drive that was not allocated (don't ask... :) ) I decided to allocate this space and modify all my partitions to better suit my needs.

To do this I ran Partition Magic from Windows ( I think that this is what broke GRUB). This process required Windows to restart, this was OK, but after completing, Partition Magic complained about an error.

I eventually was forced to shut down the machine and reboot. This resulted in GRUB error 17.  :oops:

I started Linux using the Live CD and following instructions from [http://users.bigpond.net.au/hermanzone/p15.htm#cli](http://users.bigpond.net.au/hermanzone/p15.htm#cli) (some really good stuff) I have managed to work out the following.

1.  Linux used to sit on an extended partition which Linux identified as hd(0,4)
2.  The re-partitioning exercise has changed the layouts so that the Linux partition is now
     hd(0,5).
3.  GRUB still refers to the Linux kernel as being on hd(0,4)

Lessons learnt. Don't play with partitions in Windows when you dual boot Linux...  GRUB cannot know what you have done...  (I think??)

Having booted using the Live CD and mounted all the drives (actually one drive, several partitions) I can see menu.lst in /root/grub, but I cannot save it when I try to edit it. This is a permissions issue.

How do I get to create a new menu.lst or edit the existing one??

I really don't want to re-install Linux since this is not the problem.  All my data and all my  OS'es are there and should be intact. I just need to fix menu.lst so that GRUB knows Linux is on (hd0,5) and not hd(0,4)

Any ideas ??

Thanks!!

---

### Post by DBrocks on 2008-03-27
> **Jacdeb6009 said:**
> Help... please...

I run Fiesty (7.04) together with Win XP in a dual boot setup.  Everything has been working fine for about two weeks and I am getting quite comfortable with Linux and less so with Windows :)

There was about 40Gb on my hard drive that was not allocated (don't ask... :) ) I decided to allocate this space and modify all my partitions to better suit my needs.

To do this I ran Partition Magic from Windows ( I think that this is what broke GRUB). This process required Windows to restart, this was OK, but after completing, Partition Magic complained about an error.

I eventually was forced to shut down the machine and reboot. This resulted in GRUB error 17.  :oops:

I started Linux using the Live CD and following instructions from [http://users.bigpond.net.au/hermanzone/p15.htm#cli](http://users.bigpond.net.au/hermanzone/p15.htm#cli) (some really good stuff) I have managed to work out the following.

1.  Linux used to sit on an extended partition which Linux identified as hd(0,4)
2.  The re-partitioning exercise has changed the layouts so that the Linux partition is now
     hd(0,5).
3.  GRUB still refers to the Linux kernel as being on hd(0,4)

Lessons learnt. Don't play with partitions in Windows when you dual boot Linux...  GRUB cannot know what you have done...  (I think??)

Having booted using the Live CD and mounted all the drives (actually one drive, several partitions) I can see menu.lst in /root/grub, but I cannot save it when I try to edit it. This is a permissions issue.

How do I get to create a new menu.lst or edit the existing one??

I really don't want to re-install Linux since this is not the problem.  All my data and all my  OS'es are there and should be intact. I just need to fix menu.lst so that GRUB knows Linux is on (hd0,5) and not hd(0,4)

Any ideas ??

Thanks!!

Lol, nice. Fortunately, I'm pretty sure I can help you with this.
Boot to the Linux Live CD, and mount the drives. open a terminal, and type 

```
sudo nano /boot/grub/menu.lst
```

Then edit the way you need to. Warning: Nano can be imposing, because it's text based, but it works exactly like gedit. Once you have edited it, save it, exit, reboot, and see what happens.
Good luck!

---

### Post by Jacdeb6009 on 2008-03-27
Thanks DBrocks,

This is clear :)  However, having mounted the disks, how do I actually get to access it.

That is :

    sudo nano /boot/grub/menu.lst

Simply creates a new file (on the LiveCD :) ) which of course then vannot be saved.  SImply put, from the terminal prompt, having booted from the Live CD, how do I "navigate" to the partition "hd0,5" so that I can use Nano to edit menu.lst...

I am lost.... :)

---

### Post by DBrocks on 2008-03-27
Do you know how to mount file systems in ubuntu?
Just making sure :)

Also, are you using IDE, or a SATA hard-drive?

---

### Post by louieb on 2008-03-27
Ok Grub error 17. Good news is the fix is the same as if you had installed windows after installing Ubuntu. You need to fix the MBR to find GRUB in its new location.  If you can get a [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/")
Here a good page on how to use it. [IDBS on SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")
This will help you get grub back up and running. 
Good Luck.

---

### Post by DBrocks on 2008-03-27
Lol, listen to LouieB. He has a faster solution to your plight.

---

### Post by iris-n on 2008-03-27
The problem is, ```
sudo nano /boot/grub/menu.lst
``` will give you the menu.lst of your Live CD, which obviously doesn't affect your installed system.

The Live CD mounts your partitions under /media. To know the exact command i would have to know all your partitions, but the format is: ```
sudo gedit /media/<ubuntupartition>/boot/grub/menu.lst
```

You could SuperGrub, but that's killing a fly with a shotgun.

---

### Post by DBrocks on 2008-03-27
> **iris-n said:**
> The problem is, ```
sudo nano /boot/grub/menu.lst
``` will give you the menu.lst of your Live CD, which obviously doesn't affect your installed system.

The Live CD mounts your partitions under /media. To know the exact command i would have to know all your partitions, but the format is: ```
sudo gedit /media/<ubuntupartition>/boot/grub/menu.lst
```

You could SuperGrub, but that's killing a fly with a shotgun.

Yea, thanks for clearing that up. (I'm still getting my ubuntu-legs, but trying to help people where I can)

---

### Post by louieb on 2008-03-27
> **iris-n said:**
> You could SuperGrub, but that's killing a fly with a shotgun.
Are you even getting to the GRUB menu? 
:lolflag:If not then the shotgun is by far the easiest way to go.

---

### Post by rkd on 2008-03-29
I don't believe you always would have this trouble when you change the partitions from Windows.  If the change had not changed what partition number the Linux partition was in, you would have been fine.

Anyway, I think you can fix it up easily.

Boot from the Live CD.

Open a Terminal window.

Enter the commands:```
sudo grub
find /boot/grub/stage1
```
This should display only one location.  Note that location.  For the following, I will pretend that the location it displayed was (hd0,5).  If it displays a different location, use that instead of (hd0,5).  Still in grub, enter the following:
```
root (hd0,5)
setup (hd0)
quit
```
The setup command should display six messages about its progress.  When it is done, restart the computer and your Grub should be working properly again.

What the above does is reinstall Grub.  You can find a more complete description at:

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

Herman has a lot of info on that and his other pages, but they can be hard to read.

---

### Post by Jacdeb6009 on 2008-03-31
Thanks all!!

Sorry about the "thundering silence" got a bit busy with other things.

Eventually, the advice from RKD was the simplest solution.

For some or other reason trying to get Supergrub onto a CD did not want to work (not sure why, but I will play with this some time to try and understand it).

You are right, changing partitions in Windows should not have broken Grub, but it went and renumbered the partition on the extended disk and there's the problem.

Anyway, all sorted out.

It proves that a little bit of planning goes a long way. :) The hard disk is now a complete mess, although both Ubuntu and Windows work.  I shall un-install Ubuntu, clean up all the partitions and then start over again.

Yes, this would have been the easier solution to start with, but I learnt a lot by getting Ubuntu working again, definitely worth the time and effort.

---

### Post by adrian15 on 2008-03-31
> **louieb said:**
> Ok Grub error 17. Good news is the fix is the same as if you had installed windows after installing Ubuntu. You need to fix the MBR to find GRUB in its new location.  If you can get a [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/")
Here a good page on how to use it. [IDBS on SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")
This will help you get grub back up and running. 
Good Luck.

Hi Loeuib, when menu.lst is no longer valid because partition order has changed then you cannot advise to use the Fix Boot of Linux (GRUB) options of SGD. Instead you can either tell him to try the: **Linux -> Boot of Linux Directly option** (Works 40 times out of 100) or try to edit the menu.lst manually from a live cd.

Thank you.

adrian15

---

### Post by rkd on 2008-03-31
> **adrian15 said:**
> Hi Loeuib, when menu.lst is no longer valid because partition order has changed then you cannot advise to use the Fix Boot of Linux (GRUB) options of SGD. Instead you can either tell him to try the: **Linux -> Boot of Linux Directly option** (Works 40 times out of 100) or try to edit the menu.lst manually from a live cd.

Thank you.

adrian15

Or, even better, you can use Grub from the Live CD to rebuild the Grub configuration, as I described in post #10, above.  If you have only a single hard disk and one Linux installation on your disk, that is, by far, the simplest way to solve the problem.

---

### Post by adrian15 on 2008-04-01
> **rkd said:**
> Or, even better, you can use Grub from the Live CD to rebuild the Grub configuration, as I described in post #10, above.  If you have only a single hard disk and one Linux installation on your disk, that is, by far, the simplest way to solve the problem.

In fact post #10  is incorrect. It won't work. Why? Because there has been a partition reorder and menu.lst has to be modified.

adrian15

---

### Post by rkd on 2008-04-01
> **adrian15 said:**
> In fact post #10  is incorrect. It won't work. Why? Because there has been a partition reorder and menu.lst has to be modified.

adrian15

Well, considering that Jacdeb6009 reports that the directions in post #10 fixed the problem for him or her, I find it rather odd that you claim they won't work.  Those commands rebuild menu.lst to reflect the new location of the Linux partition. They work.

---

### Post by adrian15 on 2008-04-01
> **rkd said:**
> Well, considering that Jacdeb6009 reports that the directions in post #10 fixed the problem for him or her, I find it rather odd that you claim they won't work.  Those commands rebuild menu.lst to reflect the new location of the Linux partition. They work.

I am sorry to tell you that you are still wrong. If you check Jacdeb6009 message you will see that he does not explain how he fixed his problem.

**And those commands, root and setup do not rebuild menu.lst to reflect the new location of the Linux partition, they only rebuild MBR to point to actual grub but menu.lst contents are not modified.**

I bet that he has either edited manually menu.lst file or run update-grub from a chroot environment.

***I agree with you that these commands work if partition order is NOT changed.***

adrian15

---

### Post by rkd on 2008-04-01
> **adrian15 said:**
> I am sorry to tell you that you are still wrong. If you check Jacdeb6009 message you will see that he does not explain how he fixed his problem.

**And those commands, root and setup do not rebuild menu.lst to reflect the new location of the Linux partition, they only rebuild MBR to point to actual grub but menu.lst contents are not modified.**

I bet that he has either edited manually menu.lst file or run update-grub from a chroot environment.

***I agree with you that these commands work if partition order is NOT changed.***

adrian15

Well, you are right that he only said mine was the simplest solution and that the other didn't work. That seems to indicate that my suggestion is what solved the problem, but perhaps he wasn't clear.

I still think you are wrong, but rather than argue back and forth, I'm going to go do an experiment on my test system and see whether you are right or not.  Stay tuned, as they say, though I won't be able to get to it until this evening.

---

### Post by Daveg4otu on 2008-04-01
Wish I'd read this before today...last night was also playing with the Windows partitions in Partition magic and suffered same problem Error17.

Not knowing then what I now know I  reinstalled from the CD to fix the problem - no big deal right now  as my Ubuntu install is in it's early days yet with little to configure etc., but obviously - say  6 months down the line it could be a different story.

Still trying here to persuade Partimage to  make a  backup image - so far without success.

Anyway thankyou all for an informative thread.

s

---

### Post by Duck2006 on 2008-04-01
> **Daveg4otu said:**
> Wish I'd read this before today...last night was also playing with the Windows partitions in Partition magic and suffered same problem Error17.

Not knowing then what I now know I  reinstalled from the CD to fix the problem - no big deal right now  as my Ubuntu install is in it's early days yet with little to configure etc., but obviously - say  6 months down the line it could be a different story.

Still trying here to persuade Partimage to  make a  backup image - so far without success.

Anyway thankyou all for an informative thread.

s

You can use part image.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Or the dd commands to do it.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

---

### Post by Daveg4otu on 2008-04-01
Thanks Duck2006 - it is Partimage I have been struggling with - trying to save 3.7GB of Ubuntu(on a 25GB drive) to an empty 48GB FAT32 drive - so far without success- it gets about as far as 5 or r 600MBs saved then says "Disk full".

Had a quick read thru the DD conmmands - would this work to save to a FAT32 Drive?

---

### Post by Duck2006 on 2008-04-01
Yes it will. This will give you a lot more on using the dd commands, Lots of reading.

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by rkd on 2008-04-02
This post refers back to posts #14-17

adrian15: I was wrong. You were right. 

The sequence of grub commands in post #10 does not completely correct the problem.  Before applying those commands, the error 17 happens before Grub can display the boot menu.  Those commands correct enough that the boot menu gets displayed, but when the line in the menu for selecting Ubuntu is selected, it fails at that point with error 17.

Now I'm going to go study the documentation for Grub to see whether this is the way it was intended to be or is an error in the code. It doesn't seem very good for it to correct only some of the problem, but perhaps it can't do any more than it does.

Anyway, thanks for correcting me on that. I don't want to be giving incorrect directions.

---

