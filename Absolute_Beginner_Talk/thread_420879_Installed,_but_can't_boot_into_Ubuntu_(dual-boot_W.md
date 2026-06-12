---
title: "Installed, but can't boot into Ubuntu (dual-boot Win2k)"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by timzak on 2007-04-24
Just installed Ubuntu on the 2nd SATA drive in my system.  Win2k is on the first.  However, because I didn't want to use the entire disk, I did a manual partition, selected 45GB for the / and 1GB for swap, leaving 32GB unpartitioned (plan on changing this to FAT32 to hold my DOS-based system images).  In my bios, I set the drive I installed Ubuntu on as the first to boot from, but when I boot the computer, it still loads Win2k.  No dual-boot screen ever pops up.

Could this have anything to do with my choosing a manual partition?  It seemed from the install menu that I had to choose manual if I didn't want to devote the entire disk to Ubuntu.  

I have a new VIA chipset computer (Asrock 4coreDual-VSTA) with a Core2Duo cpu.

Any and all help greatly appreciated.  BTW, I am a total newbie to Linux, so if you tell me what I should do, please also explain how to do it.  :) 

Thanks.

---

### Post by amohanty on 2007-04-24
> Just installed Ubuntu on the 2nd SATA drive in my system. Win2k is on the first. However, because I didn't want to use the entire disk, I did a manual partition, selected 45GB for the / and 1GB for swap, leaving 32GB unpartitioned (plan on changing this to FAT32 to hold my DOS-based system images). In my bios, I set the drive I installed Ubuntu on as the first to boot from, but when I boot the computer, it still loads Win2k. No dual-boot screen ever pops up.

While installing, the installer qutomatically detects that the 1st SATA is the primary master (if it is) and asks you where to install GRUB. The default is the MBR on the 1st SATA. If you picked the default I would suggest reverting the boot in your BIOS and you should get the main grub screen with _both_ ubuntu and windows boot options. 

HTH
AM

---

### Post by timzak on 2007-04-24
> **amohanty said:**
> While installing, the installer qutomatically detects that the 1st SATA is the primary master (if it is) and asks you where to install GRUB. The default is the MBR on the 1st SATA. If you picked the default I would suggest reverting the boot in your BIOS and you should get the main grub screen with _both_ ubuntu and windows boot options. 

HTH
AM

Thanks for the reply.  I tried your suggestion to revert the boot order in the bios and it did not work.  It doesn't seem to matter what SATA hdd I set as 1st in my bios; it always boots from my Win2k drive.  Is there some utility that will move this GRUB file for me?  If not, what are my other options?

By the way, what does GRUB stand for?  Like I said, I'm a complete noob.

Thanks.

---

### Post by timzak on 2007-04-24
Sorry to reply to myself but I'm afraid my message will get lost with the volume of posts here.  Should I just do a reinstall or is there something quicker I could try.  Keep in mind my newbieness...

If I do reinstall, should I do a manual partitioning again?  It seems like that's where the problem occurred.  In the interim, I tried an Ubuntu install on an old system with Win2k and it worked fine!  Why did it work on my old computer but not on my new computer.  Here are the main differences:

1) old computer has SCSI and IDE.  Win2k on SCSI, Ubuntu installed on IDE.  Dual boot works great (this grub thingy people refer to); new computer has two SATA drives.  Dual boot doesn't work (grub never shows).  Even setting other SATA drive to #1 in bios doesn't work.

2) old computer used entire drives for partitions (each OS on its own disk, using entire disk).  I also used the automated partitioning process in the installer whereas on the new computer, I chose "manual" because I thought I needed to do that so that I could leave part of the hdd unpartitioned for later use.

Do I need to choose "manual" partitioning if I don't want to dedicate the whole hdd to Ubuntu?  What I want to do is reserve a 32GB FAT32 partition for holding backup images of my Windows drive.  So the drive would look something like:
partition 1: Ubuntu swap (1GB or less)
partition 2: Ubuntu OS (46GB)
partition 3: FAT32 (32GB)

---

### Post by amohanty on 2007-04-24
You should not need to re-install, just restore GRUB to MBR:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
or
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

> 
By the way, what does GRUB stand for? Like I said, I'm a complete noob.

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)
[http://en.wikipedia.org/wiki/GRUB](http://en.wikipedia.org/wiki/GRUB)

Its a bootloader. Windows NT has one too called ntlder. However configuring ntlder to boot up linux is a bit more complicated than letting grub handle multi boots.

HTH
AM

---

### Post by ratware on 2007-04-24
Do not do a manual installation. Free some space for ubuntu and then choose the option that says "use free space for ubuntu". Try it and you will have your boot screen where you will choose windows or linux. I did it yestarday with my new laptop and it just worked fine.

---

### Post by timzak on 2007-04-24
> **amohanty said:**
> You should not need to re-install, just restore GRUB to MBR:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
or
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

.

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)
[http://en.wikipedia.org/wiki/GRUB](http://en.wikipedia.org/wiki/GRUB)

Its a bootloader. Windows NT has one too called ntlder. However configuring ntlder to boot up linux is a bit more complicated than letting grub handle multi boots.

HTH
AM

Thanks, I'll try these methods out tonight and post back if any problems.  Thanks again for the links and your time.:)

---

### Post by timzak on 2007-04-26
> **amohanty said:**
> You should not need to re-install, just restore GRUB to MBR:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
or
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

.

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)
[http://en.wikipedia.org/wiki/GRUB](http://en.wikipedia.org/wiki/GRUB)

Its a bootloader. Windows NT has one too called ntlder. However configuring ntlder to boot up linux is a bit more complicated than letting grub handle multi boots.

HTH
AM

I tried both methods from each link above, and neither worked.  The first method (the one where you don't need to use the terminal) would not let me proceed without formatting the drive.  The instructions say do not format and just keep moving forward in the menus.  But when I try to move forward without a format, it won't let me.  So I tried the 2nd method with the terminal.  I followed the instructions exactly, everything went as described in the tutorial, but when I rebooted, it STILL loaded Windows.  I tried changing the boot order in the bios to every drive (just for the heck of it).  When my Windows drive (SATA1) is set, it of course boots into Windows.  When the drive I installed Ubuntu on (SATA2) is set, I get a blinking cursor on the left edge that starts in the center of the screen and jumps down to the bottom left edge and just stays there blinking.  When I tried one of my storage drives (IDE1) it actually gave me a GRUB error message (why, I don't know when it's not the boot drive for Windows nor the drive I installed Ubuntu on).  Then when I set my 4th drive as the hdd1 in the bios, it gave me a windows error (ntldr not found).  Weird, huh?  Could it be some conflict with having two SATA drives and my bios?  I'm going to move all my data over from IDE1 to SATA2 then try installing on IDE1 and see what happens.  In the meantime, any advice would be much appreciated.

Thanks.

---

### Post by timzak on 2007-04-26
Okay, before moving 38GB of data between drives, I decided to try to NOT use manual install.  Instead, I used Guided and selected the same drive (SATA2).  Now I get a message saying "Error loading operating system" when I boot up.  If I switch the bios setting back to my Windows drive as 1st boot drive, I can load into Windows fine.  Ubuntu does NOT want to install its grub for some reason.  Now I will copy my 38GB of data from IDE1 to SATA2 and try installing on the IDE1 and see if that works.  I REALLY don't want to have to install on the same physical disk as my Windows drive.  I want Ubuntu to be separated physically, preferably on my next fastest hdd (SATA1).

I had no issues installing Ubuntu on an old spare computer (Pentium III 750Mhz) that was dual booting with Windows...I'm not sure why I can't do it on my main rig.  See a few posts above for other differences between the rigs.

---

### Post by amohanty on 2007-04-26
> When I tried one of my storage drives (IDE1) it actually gave me a GRUB error message (why, I don't know when it's not the boot drive for Windows nor the drive I installed Ubuntu on). Then when I set my 4th drive as the hdd1 in the bios, it gave me a windows error (ntldr not found). Weird, huh?

This gives us a clue. I think I mentioned above that sometimes in a multi-disk environment, especially where SATA drives are present GRUB and BIOS disagree as to what is the main drive. If on booting off of IDE1 you got the GRUB error it means that the installer installed the GRUB bootloader on IDE1 instead of SATA1 as iut should have. Its possible that for some f***ing bizarre reason grub-install identifies the IDE primary master as hd0.

One thing to try is to _remove_ IDE1 from the rig, only keep the SATAs in, and install. That 'should' put it on SATA1. It is of course possible that BIOS and GRUB may disagree again and mess up, but at least in that case you can rnu grub-install from a live cd and choose the install source via an fdisk -l

Hope I catch you before you try the whole IDE swap[ thing.

HTH
AM

---

### Post by timzak on 2007-04-26
> **amohanty said:**
> This gives us a clue. I think I mentioned above that sometimes in a multi-disk environment, especially where SATA drives are present GRUB and BIOS disagree as to what is the main drive. If on booting off of IDE1 you got the GRUB error it means that the installer installed the GRUB bootloader on IDE1 instead of SATA1 as iut should have. Its possible that for some f***ing bizarre reason grub-install identifies the IDE primary master as hd0.

One thing to try is to _remove_ IDE1 from the rig, only keep the SATAs in, and install. That 'should' put it on SATA1. It is of course possible that BIOS and GRUB may disagree again and mess up, but at least in that case you can rnu grub-install from a live cd and choose the install source via an fdisk -l

Hope I catch you before you try the whole IDE swap[ thing.

HTH
AM

I already formatted the SATA2 back to ntfs and copied the contents of IDE1 to it.  Ran out of time at that point so tonight I'm going to  go ahead and try to install on the IDE drive.

BTW, does drive imaging software work with Ubuntu and GRUB?  I'm wondering if it works on the IDE if I could just do a drive-to-drive copy with Drive Image (a program similar to Ghost) back onto the SATA drive and get it working that way.

Thanks.

---

### Post by amohanty on 2007-04-26
I have not used it so I cannot really say, but in theory it should work. You may have to munge with resetting the MBR though.

AM

---

### Post by timzak on 2007-04-27
I was able to install on my IDE drive successfully.  Still not sure why I had so much trouble with installing on my 2nd SATA drive, but for now I will stick with it on my IDE drive.  

Thanks for all the suggestions.

---

