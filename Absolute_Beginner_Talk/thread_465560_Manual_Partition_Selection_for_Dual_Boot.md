---
title: "Manual Partition Selection for Dual Boot"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by plinydogg on 2007-06-05
Hi everyone,

After the long and arduous process of figuring out how to shrink my Vista volume so that I could have some unallocated space (see this thread: [http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)) and some great help from this community, I've got another problem. Hopefully, this will be the last problem on the road to setting up the dual boot system. 

I'm under the impression that I need to choose the manual partition option during install (I think it's choice three) because if I choose to do the automatic process, it will change the Vista partition (which royally screws up Vista). My question is, what exactly do I need to do on this screen. Here's what I think I need to do:

When the partition screen comes up and I've selected the manual option, I need to:

(1) Select the "free space";
(2) Click on the "new partition" button (I think that's what it was called);
(3) Now what?

I know that I need to have a partition for ubuntu (mount it as "/") and a partition for the ubuntu swap file (what should it be mounted as). Are these logical partitions? Does the main linux partition need to be 1 GB less than the space I have available so that I can create the swap file? I guess what I'm saying is, what do I need to do exactly here?

A related question is: I've heard that GRUB messes up the Vista bootloader and prevents Vista from loading. I can't currently use my Internet from ubuntu, so if that were to happen, I wouldn't be able to seek the help of you fine people on this forum so I'd really like to avoid that if possible. 

Thanks in advance!

---

### Post by wormser on 2007-06-05
This guide might be able to help you best.  There are screen shots.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by confused57 on 2007-06-05
Follow the guide wormser suggested, specifically the "manual" partitioning section.
Here's an option to boot Ubuntu from your Vista bootloader:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

I don't have Vista myself, but I think you just have to download the EasyBCD in Vista & follow the instructions given.
If you use this method, you need to install grub to Ubuntu's root partition, not the mbr...I think there's an advanced option to select where to install grub...root partition would be something like /dev/sda2.

You shouldn't have any problems installing grub to your mbr...this will overwrite your Vista IPL on the mbr.  

I don't want to complicate matters for your first time install, but you might want to consider.  Maybe someone else can give their input, if they've set their Vista dual boot this way.

---

### Post by plinydogg on 2007-06-05
Wormser and confused: thanks for your responses. I've seen the guide that wormser posted about but the problem is that while it refers to the "manual" installation option, all it says about it is that you need a little know-how regarding partitions. If I didn't have to use the manual option then I wouldn't but since I do, I'm trying to find that "know-how." Does that make sense?

As far as EasyBCD and grub goes. Does the installation give me the option to install grub to the root partition? Because if it doesn't, then it will just overrite the Vista bootloader and I won't be able to access Vista to make the necessary changes using EasyBCD (I think?). 

Man, I'm so close and yet so far away....

---

### Post by confused57 on 2007-06-05
> **plinydogg said:**
> Wormser and confused: thanks for your responses. I've seen the guide that wormser posted about but the problem is that while it refers to the "manual" installation option, all it says about it is that you need a little know-how regarding partitions. If I didn't have to use the manual option then I wouldn't but since I do, I'm trying to find that "know-how." Does that make sense?

As far as EasyBCD and grub goes. Does the installation give me the option to install grub to the root partition? Because if it doesn't, then it will just overrite the Vista bootloader and I won't be able to access Vista to make the necessary changes using EasyBCD (I think?). 

Man, I'm so close and yet so far away....
First of all, don't be in a hurry to install Feisty...until you gather all the facts & have formulated a "game plan".

I don't use the live cd, so I can't tell you from personal experience; but, I believe when the installer reaches the install grub stage, there is an option to select "Advanced" where you can select to install grub to /dev/sda2, or whatever your root partition is designated.

If you have a Vista install DVD(not a recovery disk), you can restore the Vista IPL to the mbr.  
Here is a method of using the Ubuntu live cd to create a backup of your Vista mbr, which you can backup to a USB device or cd-rw:
[http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd](http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd)

As I mentioned, don't be in a rush to install...you should probably wait & see what other suggestions you receive in this thread.

---

### Post by Nekiruhs on 2007-06-05
Go  to System > Administration > Gnome Partition Editor
Format the unallocated space to ext3 make sure to format a partiton (double your ram size) to linux-swap
Click install, when you get to the partion screen, choose manual, select the partition you formatted to ext3 and install.

---

### Post by Inxsible on 2007-06-05
I have Vista Premium as my other OS and i used the ubuntu LiveCD, installed the grub and everything. I have no problems booting into vista (altho i do that quite rarely now :) )

Dont be paranoid about it. The grub isn't so bad :)

---

### Post by plinydogg on 2007-06-06
Everyone: thanks for your continuing help. I've taken a look at all the tutorials, posts, etc. you've pointed me to and I think I've almost got it. Here's what I plan to do at this point:

(1) Install EasyBCD in Windows Vista;
(2) Install Ubuntu via the LiveCD:
     (a) Create the main linux partition (ext3, mount as "/");
     (b) Create a linux swap file partition (ext3, mount as ???);
(3) When prompted to set up the bootloader, have GRUB installed to the bootsector ("/", right?)
(4) Reboot into Vista and add the Ubuntu entry to EasyBCD;
(5) Reboot and I should be able to select either OS.

If I understand all of this correctly, this is the ideal way to do things because it leaves the Vista bootloader intact so that if anything happens to my Ubuntu install, I'll still be able to boot into Vista. 

If this is correct, than the only thing I need to know before moving forward is

(1) What does the swap partition need to be mounted as? "linux-swap"?
(2) Will the Ubuntu installation actually ask me where I want to install GRUB (i.e., will it give me the option to install it in the bootsector instead of in the MBR)?

Thanks everyone! :) :) :)

---

### Post by dstew on 2007-06-06
Overall, that is correct, except that the format for the swap partition should be linux-swap, not ext3. And, it doesn't need to have a mount point. Otherwise, it looks good. But wait a bit for other comments. And, you will need to know the partiton name for installing grub. It will be the same name as the partition that you mount to "/". The name will be /dev/sda2 or something like that.

---

### Post by plinydogg on 2007-06-06
dstew: Thank you! I will wait for further comments but you've cleared up a lot. I didn't know that "linux-swap" was a type of file system or that I didn't need to name it. Good to know. 

Also, thanks for the heads up about needing to know the partition name. I really appreciate it!

---

### Post by confused57 on 2007-06-06
I don't think the live cd will actually "ask" you where to install grub, but there is an "advanced" button that you can click on to specify where to install grub, e.g. /dev/sda2(root partition), as dstew mentioned.
Here's someone who was using bios to boot Windows  & Ubuntu on separate hard drives, because in earlier Ubuntu version live cd's  there wasn't an option of where to install grub:
[http://ubuntuforums.org/showthread.php?t=275728](http://ubuntuforums.org/showthread.php?t=275728)

---

### Post by plinydogg on 2007-06-06
confused57: thanks for the response! I'm starting to think this thing is actually going to work out!

---

### Post by plinydogg on 2007-06-06
It worked! IT WORKED! I can dual-boot with no problems whatsoever! Thanks everyone so much for all of your help. I couldn't have done it without your help and patience. THANK YOU!

---

### Post by Inxsible on 2007-06-06
So did you install the Grub in the MBR ? or in a different location to keep your NTLDR intact ?

If you ask me: I'd much rather get rid of Windows, if not for a few of my games. So I am glad I got rid of the NTLDR and replaced it with GRUB :)

---

### Post by confused57 on 2007-06-06
> **plinydogg said:**
> It worked! IT WORKED! I can dual-boot with no problems whatsoever! Thanks everyone so much for all of your help. I couldn't have done it without your help and patience. THANK YOU!

That's what I like to hear...a happy ending, make that a happy beginning...enjoy your dual boot.

---

### Post by plinydogg on 2007-06-06
Inxsible: I installed GRUB in the bootsector of my Ubuntu partition (at least I think I did...I don't even know what a bootsector is). I left the MBR intact and then used EasyBCD to add an option to boot into either Windows or Ubuntu.

I cant' abandon Windows entirely yet because (a) I'm so new to linux; (b) I do a lot of stuff with my Pocket PC (I'm one of the bloggers with Smartphone & Pocket PC Magazine) and I don't know if Ubuntu works well with these devices (I know they work with PalmOS, but PalmOS is the WORST); and (c) I'm a gamer...I especially couldn't live without Civilization IV, Galactic Civilizations II, Morrowind, and Wolfenstein!

confused57: It is a happy beginning....I can't wait to explore this new universe!

---

### Post by HoLLyw00dGT on 2008-02-27
I'm stuck on the "Advanced" part. Do i uncheck the install boot loader box or do i change the  device to something else (currently hd0) THx

---

### Post by HoLLyw00dGT on 2008-02-27
Well i did some reading...

I mounted ext3 to (/), deleted ext2

I was left with NTFS, ext3, unallocated, and linux swap. 

In ADVANCED I selected install boot record...and typed in whatever the name for ext3 was thinking i was supposed to install it on the drive mounted "/". Apparently not and i got a "disc read error" when i rebooted, back at zero again. Doesn't anyone have the answer

---

### Post by confused57 on 2008-02-27
> **HoLLyw00dGT said:**
> Well i did some reading...

I mounted ext3 to (/), deleted ext2

I was left with NTFS, ext3, unallocated, and linux swap. 

In ADVANCED I selected install boot record...and typed in whatever the name for ext3 was thinking i was supposed to install it on the drive mounted "/". Apparently not and i got a "disc read error" when i rebooted, back at zero again. Doesn't anyone have the answer

You could use the Ubuntu live cd to install grub to the hard drive's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If you don't want to install grub to the mbr & you have a floppy drive, you could probably install grub to a floppy:
```
setup (fd0)
```

Super Grub Disk is an excellent utility for boot problems:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD is able to boot Windows or Linux, as well as install either's IPL(Initial Program Loader) to the mbr.

---

### Post by HoLLyw00dGT on 2008-02-27
Ok, I dont really understand this whole floppy thing. Other people seem to do just fine with the manual partitioning and rebooting and their being a grub menu that WORKS. But i just seem to screw it up every time. IDK what i'm doing wrong. EasyBCD is just for vista right? I shouldn't have to worry about it cuz i'm dual booting 7.10 and xp?

---

### Post by confused57 on 2008-02-27
> **HoLLyw00dGT said:**
> Ok, I dont really understand this whole floppy thing. Other people seem to do just fine with the manual partitioning and rebooting and their being a grub menu that WORKS. But i just seem to screw it up every time. IDK what i'm doing wrong. EasyBCD is just for vista right? I shouldn't have to worry about it cuz i'm dual booting 7.10 and xp?

I doubt if it's anything you're doing wrong, it's probably something to do with your system...does your XP have SP2?  The reason I ask is that I've seen people have problems booting XP with SP1 with grub.

What I would recommend is to use a Windows install cd(press "r", then FIXMBR) or Super Grub Disk and restore Window's IPL to the mbr...once you're able to boot into Windows using it's IPL, then try what I suggested to install grub to a floppy.   If the grub floppy is able to boot your Ubuntu and Windows, then it would probably be safe to install grub's IPL to the hard drive's mbr.

After you restore Windows IPL, another possiblity would be to try making a GAG floppy and try booting to Windows and Ubuntu:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)
You could try this if a grub floppy isn't able to boot Windows and Ubuntu.

GAG can also be installed to the hard drive's mbr, if it works.

---

### Post by Duck2006 on 2008-02-27
> The reason I ask is that I've seen people have problems booting XP with SP1 with grub.

I run win xp with no sp2 or updatas and could run grub no prob's, but just cause it worked for me it may not work on all systems.

---

### Post by confused57 on 2008-02-27
> **Duck2006 said:**
> I run win xp with no sp2 or updatas and could run grub no prob's, but just cause it worked for me it may not work on all systems.
Thanks, that's good to know...the thread is so old that I read about difficulties booting XP from grub until they updated to SP2, I'd never be able to find it...it's possible SP1 wasn't even installed.   I was mainly trying to dig for some more info from the poster I replied to.

---

