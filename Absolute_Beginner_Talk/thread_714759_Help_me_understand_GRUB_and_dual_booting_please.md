---
title: "Help me understand GRUB and dual booting please"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by lambono on 2008-03-04
Hi guys,
First of all let me start by saying I have read plenty of guides and how to's on this topic... but there are few things I still don't understand...

This is the impression I have so please correct me where Im wrong..
I have a primary hard drive with windows XP. 
There are files at the very start of the drive called the Master Boot Record and these tell the computer where to load Windows. 

Then comes along ubuntu on a second hard drive... 
When I installed this did I wipe the MBR on the windows drive and instead tell the computer to look in /boot of my second disc? 
As a result of this, if I unplug the linux disc I get the error Disc Boot Failure or if I unplug the windows disc I get the error Error Loading Grub. 
Could I have avoided this by having the linux disc as the primary disc and just modify its MBR, then I could leave the windows MBR alone? 

What happens If I reinstall windows, will I loose access to the linux disc? And how would I fix it to dual boot it again. 

What happens if I reinstall linux? Will everything just work as normal? 

Now heres the big question I need to know... 
Currently my linux hard drive is faulty, its old and as always given me problems with linux and windows. If i unplug this drive and replace it with a new one (was thinking of getting Western Digital Green Power Caviar 500GB) and install Ubuntu, will windows and linux just work together as before? And more importantly, if I need to revert back to my old drive, would it be a simple case of unplugging the new one and replacing it with the new one? 
I only have room for 2 drives so cant keep them all in the machine at the same time.

I know thats a lot of questions, so thanks in advance for anyone who is able to help me.

Cheers,
Lambono

---

### Post by mikewhatever on 2008-03-04
> **lambono said:**
> 
When I installed this did I wipe the MBR on the windows drive and instead tell the computer to look in /boot of my second disc?

Yes, that's what usually happens.

> As a result of this, if I unplug the linux disc I get the error Disc Boot Failure or if I unplug the windows disc I get the error Error Loading Grub. 
Could I have avoided this by having the linux disc as the primary disc and just modify its MBR, then I could leave the windows MBR alone?

Not sure master/slave is the issue here. You can actually specify where to install the MBR part of GRUB during the installation, but having two separate bootloaders and two separate MBRs would not be very convenient. You'd have to enter BIOS every time to chose the disk to boot from.

> What happens If I reinstall windows, will I loose access to the linux disc? And how would I fix it to dual boot it again.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29)

> What happens if I reinstall linux? Will everything just work as normal?

Similar to the first install, the new one should automatically detect Windows and add an entry to GRUB's menu. You might want to backup the current one to be on the safe side.

> Now heres the big question I need to know... 
Currently my linux hard drive is faulty, its old and as always given me problems with linux and windows. If i unplug this drive and replace it with a new one (was thinking of getting Western Digital Green Power Caviar 500GB) and install Ubuntu, will windows and linux just work together as before? And more importantly, if I need to revert back to my old drive, would it be a simple case of unplugging the new one and replacing it with the new one? 
I only have room for 2 drives so cant keep them all in the machine at the same time.

The new installation should work as specified above, but switching the drives is not a good idea. Your /etc/fstab entries would not match.

---

### Post by rug77 on 2008-03-04
I think it all works like this (and I'm sure I'll be corrected if I'm wrong) ...

The Master boot record tells the PC where to find a program to run, which then loads the operating system.  On Windows machines, this points to the windows loader on the primary drive.

Loading Ubuntu has overwritten the MBR to point to a program called Grub on whatever drive the Ubuntu install is on.  This uses configuration files to point to the O/S loader programs available.

Remove the Ubuntu disk, and the MBR will point into empty space, and won't work.  Remove the Windows disk, and you've taken away the MBR, so it won't load.

Replace the current Ubuntu disk with a new replacement and install Ubuntu on it, and you'll be able to swap the two Ubuntu disks and still have the system work as expected.

To get rid of the grub process, boot from the Windows disk, go into Recovery console, and type FIXMBR to return the MBR to the windows standard.

I hope this answers the question, and I also hope it is correct enough for me not to be buried under a pile of scorn :-D

EDIT :  Beaten to it with a faster, and better, answer ...

---

### Post by stalkingwolf on 2008-03-04
> I only have room for 2 drives so cant keep them all in the machine at the same time.


You might invest in a USB enclosure for your old drive.  Then you can plug it in at will or leave it connected.
I just got one . I will let you know how it works.  The investment is small I paid under $10.00 +
shipping on ebay.

---

### Post by lambono on 2008-04-14
> 
You might invest in a USB enclosure for your old drive. Then you can plug it in at will or leave it connected.
I just got one . I will let you know how it works. 


So finally got myself that USB enclosure. 
What next? How do I boot into my old linux install!? 
Thanks for your help!!!

---

