---
title: "I'm trying to reinstall Windows but..."
date: 2011-05-08
forum: Any Other OS
---

### Post by jgold98 on 2011-05-08
OK... So I put in my HP recovery CD's for my HP Pavillion Elite e9260f Desktop. And I went through the process, but at the end I get a black screen that says
 
error: Unknown Filesystem
grub recue>_
 
OK, so is there a magic command that will help me? Or can I try using Derek's Boot and Nuke and then use the CD's again?
 
***By the way I'M NOT DUAL BOOTING***

---

### Post by ivanovnegro on 2011-05-08
You have to format your hard drive back to NTFS to be able to reinstall Windows, Ubuntu uses Ext4 as file system.

---

### Post by jgold98 on 2011-05-08
How do I do that?

---

### Post by Anonymous is Incognito on 2011-05-08
Formatting can be done with a lot of tools.

I recommend you use GParted from a LiveCD. You **will** loose your data, back it up first!

You can find it under System -> Administration -> GParted

---

### Post by ivanovnegro on 2011-05-08
You have some possibilities to do that, I have to admit, I never went back to Windows.
You could use the program Gparted to make an NTFS partition for Windows, I think you can also use the Live Ubuntu CD for that.
First of all, make a backup of all your data.
[Here]("https://help.ubuntu.com/11.04/index.html") the Ubuntu documentation, there is also a documentation from Microsoft how to reinstall Windows after Ubuntu but now I cannot find it.

PS: As it is an Ubuntu Forum, can I ask you what problems you had with it before reinstalling the whole system? Maybe we can help sort your problems out with Ubuntu.

---

### Post by wilee-nilee on 2011-05-08
> **jgold98 said:**
> OK... So I put in my HP recovery CD's for my HP Pavillion Elite e9260f Desktop. And I went through the process, but at the end I get a black screen that says
 
error: Unknown Filesystem
grub recue>_
 
OK, so is there a magic command that will help me? Or can I try using Derek's Boot and Nuke and then use the CD's again?
 
***By the way I'M NOT DUAL BOOTING***

Okay is the recovery using a set of discs or image on a hard drive you have saved an image with?

Is the disc for triggering a recovery partition?

Lets say you have a recovery partition, and you pull out the trusty partitioner and wipe it when it is what you actually need, see where I'm going here.

What if your reinstalled, recovered and all you need is the ms bootloader in the mbr? A grub prompt does not mean you need to reformat the HD all by itself necessarily it at the least means grub is in the mbr.

So from a booted live Ubuntu cd, thumbdrive, or Ubnutu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by jgold98 on 2011-05-08
> **ivanovnegro said:**
> You have some possibilities to do that, I have to admit, I never went back to Windows.
You could use the program Gparted to make an NTFS partition for Windows, I think you can also use the Live Ubuntu CD for that.
First of all, make a backup of all your data.
[Here]("https://help.ubuntu.com/11.04/index.html") the Ubuntu documentation, there is also a documentation from Microsoft how to reinstall Windows after Ubuntu but now I cannot find it.
 
PS: As it is an Ubuntu Forum, can I ask you what problems you had with it before reinstalling the whole system? Maybe we can help sort your problems out with Ubuntu.
 I want to use .exe files, I have wine but it doesn't work on 75% of the programs I use, and I need Netflix to watch anything, which sucks on Ubuntu. I also just like Windows better. Don't get me wrong I love it, but VERY low accessibility for me, I don't like having to spend 2 hours trying to install MM8BDM or DOOM.

---

### Post by Elfy on 2011-05-08
moved out of ubuntu support sub-forums

---

### Post by ivanovnegro on 2011-05-08
> **jgold98 said:**
> I want to use .exe files, I have wine but it doesn't work on 75% of the programs I use, and I need Netflix to watch anything, which sucks on Ubuntu. I also just like Windows better. Don't get me wrong I love it, but VERY low accessibility for me, I don't like having to spend 2 hours trying to install MM8BDM or DOOM.

Its ok, you have accetable reasons.
I think try what wilee-nilee suggested.

---

### Post by jgold98 on 2011-05-08
> **ivanovnegro said:**
> Its ok, you have accetable reasons.
I think try what wilee-nilee suggested.
 OK. But if I don't want to do that, Can I use DBAN to completely wipe the hard disk. Then try to use the recovery disk?

---

### Post by wilee-nilee on 2011-05-08
> **jgold98 said:**
> OK. But if I don't want to do that, Can I use DBAN to completely wipe the hard disk. Then try to use the recovery disk?

So is the recovery disc a full install disc?

If it isn't then what are your trying to recover?

Is it a saved image...etc, a just plain recovery disc does no more then get you to a saved OS to fix or reinstall, it does not actually install unless it is a install disc.

You're fixated on the grub prompt, it is a problem but you do not have to wipe the disc with dban at this point as far as I see.

---

### Post by jgold98 on 2011-05-08
> **wilee-nilee said:**
> So is the recovery disc a full install disc?
 
If it isn't then what are your trying to recover?
 
Is it a saved image...etc, a just plain recovery disc does no more then get you to a saved OS to fix or reinstall, it does not actually install unless it is a install disc.
 
You're fixated on the grub prompt, it is a problem but you do not have to wipe the disc with dban at this point as far as I see.
 
Here's the story: I had Windows 7, wanted to try Ubuntu. I accidentally used my entire partition. So I gotthese disk that will put it back to it's original factory settings. So all I want to do is start over COMPLETELY. AND I'll see if I can find my Ubuntu disk.
 
I also used GParted live disk to reformat it to NTSF

---

### Post by snerd on 2011-05-08
If you're seeing the grub prompt, your machine is not booting from the CD drive. You need to go into settings and set it to boot from CD drive first.

---

### Post by jgold98 on 2011-05-08
> **snerd said:**
> If you're seeing the grub prompt, your machine is not booting from the CD drive. You need to go into settings and set it to boot from CD drive first.
 I did

---

### Post by wilee-nilee on 2011-05-08
> **jgold98 said:**
> Here's the story: I had Windows 7, wanted to try Ubuntu. I accidentally used my entire partition. So I gotthese disk that will put it back to it's original factory settings. So all I want to do is start over COMPLETELY. AND I'll see if I can find my Ubuntu disk.
 
I also used GParted live disk to reformat it to NTSF

If it is not a full install disc or the OEM disc you can't do anything. 

I think you have a recovery disc that is just the tool to get to saved images or a recovery partition.

Put that disc in another computer running a OS look in the properties of the disc, if it is less than 2.7 gigs, you have a disc that will not install W7.

---

### Post by jgold98 on 2011-05-08
> **wilee-nilee said:**
> If it is not a full install disc or the OEM disc you can't do anything. 
 
I think you have a recovery disc that is just the tool to get to saved images or a recovery partition.
 
Put that disc in another computer running a OS look in the properties of the disc, if it is less than 2.7 gigs, you have a disc that will not install W7.
 
It's 3 4.7 gig disk, all full and 1 Supplemental Recovery Disk. I got those disk because my recovery partition is gone and it looks like Windows on the installation, but it's HP. So if you know any Windows commands I can use somehow on that to delete the Ext2 that would help a lot. I would know these work because a technician for HP gave them to me. And he knows nothing about Ubuntu Linux, so I turned to you guys. So it has nothing to do with the disk. He said it should have re-partitioned over my Linux, which I'm pretty sure it did so I have 3 questions:
 
1.) Any Windows commands to use on 'Reset" disk?
2.)Did it re-partition over it?
3.)Tell me how to use GParted to re-format the ext2

---

### Post by wilee-nilee on 2011-05-08
> **jgold98 said:**
> It's 3 4.7 gig disk, all full and 1 Supplemental Recovery Disk. I got those disk because my recovery partition is gone and it looks like Windows on the installation, but it's HP. So if you know any Windows commands I can use somehow on that to delete the Ext2 that would help a lot. I would know these work because a technician for HP gave them to me. And he knows nothing about Ubuntu Linux, so I turned to you guys. So it has nothing to do with the disk. He said it should have re-partitioned over my Linux, which I'm pretty sure it did so I have 3 questions:
 
1.) Any Windows commands to use on 'Reset" disk?
2.)Did it re-partition over it?
3.)Tell me how to use GParted to re-format the ext2

Okay finally we get the information that is pertinent.

From what I understand here you have reinstalled using this disc, and now get a grub prompt.

I would like to see the bootscript in my signature run to be honest you have your cart before the horse here.

What you want is easily done but you have to follow some basic protocol for us to help.

I have W7 and XP and a bunch of open source installed on one HD, I'm not just blowing smoke out of the side of my neck here.

So from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

You may have windows installed and just need the mbr loaded, you can try this to load the ms bootloader to the mbr.


1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
```
BootRec.exe /fixmbr
``` 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by jgold98 on 2011-05-08
> **wilee-nilee said:**
> Okay finally we get the information that is pertinent.
 
From what I understand here you have reinstalled using this disc, and now get a grub prompt.
 
I would like to see the bootscript in my signature run to be honest you have your cart before the horse here.
 
What you want is easily done but you have to follow some basic protocol for us to help.
 
I have W7 and XP and a bunch of open source installed on one HD, I'm not just blowing smoke out of the side of my neck here.
 
So from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.
 
You may have windows installed and just need the mbr loaded, you can try this to load the ms bootloader to the mbr.
 
 
1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
```
BootRec.exe /fixmbr
``` 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
 I don't have a disk big enough to make a Ubuntu Live CD

---

### Post by wilee-nilee on 2011-05-08
> **jgold98 said:**
> I don't have a disk big enough to make a Ubuntu Live CD

Try the command, to reload the mbr.

It may be that the disc you have does not reload the mbr but that would be really strange, I mean doesn't MS want you using MS, having no ability to boot it is counter-productive.

I will say though that I had a XP oem disc set that would not install without wiping the disc completely, including the first 512MB=the mbr. I used dban for this dereks probably does the same you may be correct in needing to wipe it really spiffy clean, including the mbr.

You mention a ext2 what is that? it is a partition I just don't know how you are viewing what it is and its role here. Was the ext2 a boot partition?

---

### Post by jgold98 on 2011-05-08
> **wilee-nilee said:**
> Try the command, to reload the mbr.
 
It may be that the disc you have does not reload the mbr but that would be really strange, I mean doesn't MS want you using MS, having no ability to boot it is counter-productive.
 
I will say though that I had a XP oem disc set that would not install without wiping the disc completely, including the first 512MB=the mbr. I used dban for this dereks probably does the same you may be correct in needing to wipe it really spiffy clean, including the mbr.
 
You mention a ext2 what is that? it is a partition I just don't know how you are viewing what it is and its role here. Was the ext2 a boot partition?
 ext2 (I think that's what it's called) is like the NTFS of Linux. So I should use DBAN? And if I do, can I still retry the Recovery Disk? Or should I use this Super Grub Disk I found online? DBAN is my last resort, because it could screw me in.

---

### Post by wilee-nilee on 2011-05-08
> **jgold98 said:**
> ext2 (I think that's what it's called) is like the NTFS of Linux. So I should use DBAN? And if I do, can I still retry the Recovery Disk? Or should I use this Super Grub Disk I found online? DBAN is my last resort, because it could screw me in.

If all you want is MS on the HD, generally just wiping the disc with gparted should work, the recovery with the 3 other discs containing the OS should build the correct partitions, at the install. But.....

As I said though I had a problem with an XP oem set which is what you seem to have (OEM reinstall discs) wiping the disc with dban fixed this and I was able to install.

All dban does is wipe it clean all of it including the mbr which gparted doesn't. Dban also wipes info on the disc by doing a deep wipe with 1's and 0's I believe it is for a squeaky clean so to speak not traceable, or recoverable as far as what was there.

So you have no proof of a ext2 partition, it has not been used for a long time, so I doubt you had one, ext3 or ext4 is more likely.

I think think the ope discs are thrown off by the mbr not being clean of grub, or a MS bootloader being there, dban, or I suspect dereks will wipe that and you will be good to go, I doubt you have to build a partition schema first the OEM set should do this automatically.

You may be installed and just need the MS bootloader put in the mbr, hard to say without a picture of the HD from gparted or the boot script, or the command run and posted from a booted live cd the gparted will work here.
fdisk -l

---

### Post by jgold98 on 2011-05-08
> **wilee-nilee said:**
> If all you want is MS on the HD, generally just wiping the disc with gparted should work, the recovery with the 3 other discs containing the OS should build the correct partitions, at the install. But.....
 
As I said though I had a problem with an XP oem set which is what you seem to have (OEM reinstall discs) wiping the disc with dban fixed this and I was able to install.
 
All dban does is wipe it clean all of it including the mbr which gparted doesn't. Dban also wipes info on the disc by doing a deep wipe with 1's and 0's I believe it is for a squeaky clean so to speak not traceable, or recoverable as far as what was there.
What about Super Grub Disk?

---

### Post by jgold98 on 2011-05-08
> **jgold98 said:**
> What about Super Grub Disk?
 I still get ```
error: unknown filesystem
grub rescue>_
```

---

### Post by wilee-nilee on 2011-05-08
> **jgold98 said:**
> What about Super Grub Disk?

Super grub is for getting into a OS that wont boot, with Linux you can't delete it while running.

To be honest here if you look through this thread the answers are all here. Wipe the hd with dban and install.

We are way out of any normal way of dealing with this I.E. you don't have a regular Ubuntu disc, your best tool even if running MS alone.

I'm going to disconnect at this point I don't have the patience, to follow you around when I have given the answers, best of luck.;)

We are at 24 posts on a 3 post problem.

I'm surprised this thread has not been closed the only thing relevant is a grub prompt, your installing windows go here there is great quick help.;)
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by jgold98 on 2011-05-08
> **wilee-nilee said:**
> Super grub is for getting into a OS that wont boot, with Linux you can't delete it while running.
 
To be honest here if you look through this thread the answers are all here. Wipe the hd with dban and install.
 
We are way out of any normal way of dealing with this I.E. you don't have a regular Ubuntu disc, your best tool even if running MS alone.
 
I'm going to disconnect at this point I don't have the patience, to follow you around when I have given the answers, best of luck.;)
 
We are at 24 posts on a 3 post problem.
 
I'm surprised this thread has not been closed the only thing relevant is a grub prompt, your installing windows go here there is great quick help.;)
[http://www.sevenforums.com/](http://www.sevenforums.com/)
 OK Thanks

---

