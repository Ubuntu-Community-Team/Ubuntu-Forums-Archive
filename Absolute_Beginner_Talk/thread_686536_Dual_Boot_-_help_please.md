---
title: "Dual Boot - help please"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by xioSlayer on 2008-02-03
Ok, first and foremost, I have read many of the similar posts on this forum, but do not understand most of the things that writers assume that the reader already knows.  Can someone help me and explain every step along the way?

I have 2 SATA hard drives, one of which has a working XP installation on it, and one of which has the attempt that I made at installing Ubuntu on it.

What is the best way for me to be able to have dual boot?

[B]Here is what I have done so far:

1.  started ubuntu in safe graphics mode.
2. Installed it with guided partitioning help onto my second HDD.
3. Went into my BIOS and changed the hard drive priority to make the Ubuntu drive number 1.
4. Attempted to boot only to have my BIOS tell me "Error loading operating system."
5. I switched back the priority to the windows drive, and that is where I am now, with a working windows and a non-working ubuntu.[/B]

Here are my system specs (in case it matters)
[B]Intel Core2Duo e6750 @ 3.2ghz
XFX 650i nForce MoBo
2 X 1GB Corsair XMS2 RAM @ 800mhz 4-4-4-12
XFX 8800 GT 512mb[/B]

Thanks in advance.

---

### Post by iansane on 2008-02-03
Might be different for you but BIOS boot priority didn't have anything to do with my dual boot.
The first drive with window on it is set as master and the second one with ubuntu is set as slave.

The installation from the live cd automatically installed Grub on hd0 which is the first one. I tend to think the problem is something to do with master/slave settings on the drives if they are both internal.

---

### Post by xioSlayer on 2008-02-03
so.... how do I fix what I have done and make it do what I wish?

---

### Post by DiscGo on 2008-02-03
You need to have both operating systems on the same drive.


You'll need to partition your primary drive to have space for both operating systems. Vista requires 40 gigabytes and it will fill 15 gig with the OS. Ubuntu requires 2 gig but I recommend you split your primary drive.

---

### Post by xioSlayer on 2008-02-03
So you can't dual boot with two separate HDs? period?

---

### Post by Moop on 2008-02-03
You can dual boot with two different hard drives. I don't know why grub didn't work on your install but it can be fixed from a live cd. 

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by snick_hill on 2008-02-03
FYI: the computer "posts" and loads the operating system with the help of the BIOS. the BIOS detects both your hard drives but loads the operating system of only the primary drive. At any given point, not more than one hard drive can be your primary drive. therefore, only the operating system on the primary drive loads up.

in simple words: No, you cannot have an  operating system on each drive. all of them should only be in one hard drive. :)

---

### Post by bumanie on 2008-02-03
> So you can't dual boot with two separate HDs? period? 
You can dual boot in this manner. 
Windows prefers to be on the primary hard drive on the first partition of that hard drive - You have that according to your post.
1.Did you have both drives plugged in to power when you installed ubuntu or did you unplug the windows drive whilst installing ubuntu?
2. From where you are now, I would reinstall ubuntu. Ensure both drives are plugged in and grub (linux bootloader) should recognise your xp install and then at boot up give you the choice of which OS to boot. There should not be a need to start in safe graphics mode.

---

### Post by Moop on 2008-02-03
> **snick_hill said:**
> FYI: the computer "posts" and loads the operating system with the help of the BIOS. the BIOS detects both your hard drives but loads the operating system of only the primary drive. At any given point, not more than one hard drive can be your primary drive. therefore, only the operating system on the primary drive loads up.

in simple words: No, you cannot have an  operating system on each drive. all of them should only be in one hard drive. :)

That's not right. I use different hard drives to triple boot. The operating systems do not have to be on the same hard drive.

---

### Post by jaybirdUK on 2008-02-03
I tried to create a dual boot yesterday, but have to disconnect my XP drive when launching Ubunto, otherwise it just launches straight into XP without even finding the dual boot menu, not sure how to resolve this.

Sorry for hijacking this thread, but it is relative to my issue :(

---

### Post by Moop on 2008-02-03
> **jaybirdUK said:**
> I tried to create a dual boot yesterday, but have to disconnect my XP drive when launching Ubunto, otherwise it just launches straight into XP without even finding the dual boot menu, not sure how to resolve this.

Sorry for hijacking this thread, but it is relative to my issue :(

It's probably because when you connect your XP drive your bios boots it first. Try connecting both drives and entering bios setup and set the Ubuntu drive to boot first.

---

### Post by bumanie on 2008-02-03
Both of you should look at this [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) It is very long but it tells you all about grub and how it can boot mutiple OSes.

---

### Post by jaybirdUK on 2008-02-03
> **Moop said:**
> It's probably because when you connect your XP drive your bios boots it first. Try connecting both drives and entering bios setup and set the Ubuntu drive to boot first.

The Ubunto drive doesn't even show in the bios, I think it's because windows is on a Sata & Ubunto is on an IDE, I wanted them on different drives so I don't have to mess about with my Windows drive, but I
 think I may have to put a partition on that & install ubunto there.

---

### Post by bumanie on 2008-02-03
Read the above link. It talks about grub being confused when there is a mixture of sata and ide drives and gives suggestions how to fix it.

---

### Post by xioSlayer on 2008-02-03
I attempted to reinstall but no luck.  I have to use the "Safe Graphics" mode or else ubuntu says its loading its kernel then the screen turns black and stays that way.

Please help.

---

### Post by fmartinez on 2008-02-03
XioSlayer... are you still having issues? i've installed ubuntu and  xp this is how i did it: 
1. make sure XP is already installed and operation on the primary hard disk. 
2. make sure you have unallocated space on the 2nd hard disk
3. when you begin to install make sure you install Ubuntu on the 2nd hard disk's free space.
4. Ubuntu will take care of the rest as far installing grub on the right partition and so forth.... it was pretty straight forward and i've done this a couple times with no issue.

---

### Post by xioSlayer on 2008-02-03
How do I know which hard drive is the primary one?

---

### Post by bumanie on 2008-02-03
> I attempted to reinstall but no luck. I have to use the "Safe Graphics" mode or else ubuntu says its loading its kernel then the screen turns black and stays that way.
It seems that ubuntu is having trouble with your graphics card. Nvidia do have a linux driver for that card, but that doesn't help if you can't install the OS. You could try the alternate cd which is text based and doesn't involve a live cd. If you can get the OS installed and bootable, even if the graphics are still no good, it then should be fixable by turning off x server and going into console and installing the driver that way. You may have to wait for someone more knowledgeable than me to help you, but often the alternate cd will install when the live cd won't. But I don't know whether it will overcome the graphics card issue or not. What fmartinez said, is what I would expect to occur in most circumstances - your graphics card seems to be the sticking point. See if you can install in safe graphics mode. I've not heard of anyone installing that way before, but it could work.

---

### Post by xioSlayer on 2008-02-03
> **bumanie said:**
> It seems that ubuntu is having trouble with your graphics card. Nvidia do have a linux driver for that card, but that doesn't help if you can't install the OS. You could try the alternate cd which is text based and doesn't involve a live cd. If you can get the OS installed and bootable, even if the graphics are still no good, it then should be fixable by turning off x server and going into console and installing the driver that way. You may have to wait for someone more knowledgeable than me to help you, but often the alternate cd will install when the live cd won't. But I don't know whether it will overcome the graphics card issue or not. What fmartinez said, is what I would expect to occur in most circumstances - your graphics card seems to be the sticking point. See if you can install in safe graphics mode. I've not heard of anyone installing that way before, but it could work.

It doesn't work in the other mode, I've already tried safe graphics mode 3 times (which is the only mode that shows something)  It boots from the live CD fine and I install it, I just can't figure out how to boot from it.

---

### Post by iansane on 2008-02-07
> **snick_hill said:**
> FYI: the computer "posts" and loads the operating system with the help of the BIOS. the BIOS detects both your hard drives but loads the operating system of only the primary drive. At any given point, not more than one hard drive can be your primary drive. therefore, only the operating system on the primary drive loads up.

in simple words: No, you cannot have an  operating system on each drive. all of them should only be in one hard drive. :)

Yes you can. I'm using two seperate drives now. One of them is a rigged up laptop harddrive. The first one is set as master and had windows already on it. The second one is on the same IDE but is set as a slave. I used windows to delete all partitions on it first and then put in the live CD. It detected them and installed perfectly. That's why the grub menu entries for Windows and Ubuntu are hda and hdb.

---

