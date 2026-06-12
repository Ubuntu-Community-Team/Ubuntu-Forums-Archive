---
title: "UBUNTU or something RUINED my harddrive!"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-12-27
I installed ubuntu and some other operating system (think mac), 
and now when i try to insert a fresh xp pro cd into my laptop to try to wipe out everything, I get a windows stop error. ("Stop 0x0000007B")
I tried server 2003 install and it said it couldn't find a hard drive to install it to.. Maybe I ruined my MBR? Did grub do this? 

How do I fix this?

I just want to tell xp, "HEY just wipe out everything i don't give a crap"!!

---

### Post by SOULRiDER on 2007-12-27
It is possible that server 2003 doesnt ahve drivers for your hard drive, sad but true.

---

### Post by systemintheglitch on 2007-12-27
Ummm.
I tried both xp and server..

And I've tried all the obvious stuff like booting to gparted live cd and deleteing all partitions..

One interesting thing is that if i DON"T boot off of the xp cd it goes to grub! So that's still in the mbr..

---

### Post by systemintheglitch on 2007-12-27
> **SOULRiDER said:**
> It is possible that server 2003 doesnt ahve drivers for your hard drive, sad but true.

Oh yah..

I would imagine xp would have it. I don't know for sure.. but it's am ibm laptop x60tablet not something UNcommon.

---

### Post by meierfra on 2007-12-27
To remove grub from the MBR click on "FixMBR" in my signature.

---

### Post by thavid on 2007-12-27
Something like BIOS MBR Protection!? Older Compaq notebooks had that... You can try a low level format, or try to connect the hard drive through an USB support and then, via livecd, wipe everything and just to be certain, create some 10 or 20 GB FAT32 partition (obviously to be deleted during XP Setup)

---

### Post by sid351 on 2007-12-27
Don't blame Ubuntu, or "something else", that's just ignorant.

Also, legit Mac OS on a non-apple-laptop?  ...Sure.

With Grub still coming up it sounds like you've still got a partition somewhere.

Is your laptop set to boot off CD first?

What exactly comes up on the screen?

---

### Post by meierfra on 2007-12-27
> 
With Grub still coming up it sounds like you've still got a partition somewhere.

Why? One part of Grub  sits in the MBR. And none of the  things the OP did would remove Grub from the MBR.

---

### Post by sid351 on 2007-12-27
> **meierfra said:**
> Why? One part of Grub  sits in the MBR. And none of the  things the OP did would remove Grub from the MBR.

...Isn't the MBR a partition?

Actually, on re-read I'm confused.  The OP hasn't stated if there is still an OS on the system or not, just that he is having issues with the Windows discs.

What exactly is the problem?  Does the OS not load off the Grub menu?

---

### Post by LaRoza on 2007-12-27
> **sid351 said:**
> ...Isn't the MBR a partition?

Actually, on re-read I'm confused.  The OP hasn't stated if there is still an OS on the system or not, just that he is having issues with the Windows discs.

What exactly is the problem?  Does the OS not load off the Grub menu?

No, it is a sector.

If you were able to install Ubuntu on the laptop with a CD, but can't install Windows, I would say it is the Windows disks problem. As stated before, it may not have drivers.

---

### Post by meierfra on 2007-12-27
> ..Isn't the MBR a partition?

No, it is the first sector of the hard drive and comes before any of the partitions. So deleting all the partitions, will not erase the MBR.

---

### Post by sid351 on 2007-12-27
> **LaRoza said:**
> No, it is a sector.

If you were able to install Ubuntu on the laptop with a CD, but can't install Windows, I would say it is the Windows disks problem. As stated before, it may not have drivers.

My bad.  Looks like I need to re-revise.

Damn COMP Tia book with it's 500 pages.

Next time I shan't just jump in.  I apologise.

---

### Post by LaRoza on 2007-12-27
> **sid351 said:**
> My bad.  Looks like I need to re-revise.

Damn COMP Tia book with it's 500 pages.

Next time I shan't just jump in.  I apologise.

Try the Mike Myers Passport books, or Scott Mueller's [http://www.amazon.com/Upgrading-Repairing-PCs-18th/dp/0789736977/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1198803869&sr=8-1](http://www.amazon.com/Upgrading-Repairing-PCs-18th/dp/0789736977/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1198803869&sr=8-1)

I recommend the Second for information, great book

---

### Post by louieb on 2007-12-27
If i remember right. Use GParted to create a partition and format it NTFS. Then your XP install CD should work.

---

### Post by systemintheglitch on 2007-12-27
There is no remaiing os on the disk.
I can boot from cd, which i can do with the xp install, and i've tried two different xp cd's.

I don't see how xp can not have my drivers. How do they expect people to install xp on their computers. My computer IS a common computer..

And to whoever made the claim, i am not blaming ubuntu, i am blaming my irresponsible use of it. I thought that would have been either implied or assumed.

---

### Post by LaRoza on 2007-12-27
> **systemintheglitch said:**
> 
I don't see how xp can not have my drivers. How do they expect people to install xp on their computers. My computer IS a common computer..

And to whoever made the claim, i am not blaming ubuntu, i am blaming my irresponsible use of it. I thought that would have been either implied or assumed.

You'd be surprised, Windows is usually an OEM install, and XP doesn't have drivers for some common hard disk set ups. The fix is to have the drivers on a floppy or something. I don't know if this is your problem.

You can try reformatting the disk as NTFS, with GParted. That may fix it.

---

### Post by systemintheglitch on 2007-12-27
> **louieb said:**
> If i remember right. Use GParted to create a partition and format it NTFS. Then your XP install CD should work.

I tried that.
I tried all the obvious things.

---

### Post by LaRoza on 2007-12-27
> **systemintheglitch said:**
> I tried that.
I tried all the obvious things.

Have checked the install disk? I am running out of ideas of what could be the trouble.

---

### Post by SOULRiDER on 2007-12-27
> **systemintheglitch said:**
> There is no remaiing os on the disk.
I can boot from cd, which i can do with the xp install, and i've tried two different xp cd's.

I don't see how xp can not have my drivers. How do they expect people to install xp on their computers. My computer IS a common computer..

And to whoever made the claim, i am not blaming ubuntu, i am blaming my irresponsible use of it. I thought that would have been either implied or assumed.

I've seen XP not having drivers for several computer's hard drives.

---

### Post by Moop on 2007-12-27
Maybe one of the hard drive mfg's bootable cd's would put your hard drive back in shape for XP. Western Digital and Seagate both have good ones.

If your hard drive is a sata type it's possible that an early XP cd wouldn't recognize it. XP started recognizing sata hard drives with either SP1a or SP2. You could make a new install cd with SP2 integrated.

---

### Post by systemintheglitch on 2007-12-27
> **SOULRiDER said:**
> I've seen XP not having drivers for several computer's hard drives.

Really? That's unfortunate, 

then do you suppose that the cause is that grub is still on the mbr?
that is where I installed it to..
I want to use ms-sys, but i don't want to download ubuntu iso again.. What about ubuntu server? Does that have it?

---

### Post by LaRoza on 2007-12-27
> **systemintheglitch said:**
> Really? That's unfortunate, 

then do you suppose that the cause is that grub is still on the mbr?
that is where I installed it to..
I want to use ms-sys, but i don't want to download ubuntu iso again.. What about ubuntu server? Does that have it?

You can get the Super Grub Disk which will restore the Windows MBR, but that isn't the problem I think.

The link in my sig has the lnk to the download page.

---

### Post by systemintheglitch on 2007-12-27
If you really think it doesn't have drivers for my laptop, and that is the problem.. I dunno.. It seems kind of fishy.. I mean, another os that shall remain nameless (that is typically never installed on an ibm, and im not talkin about linux) works just fine on my harddrvie.

---

### Post by systemintheglitch on 2007-12-27
Oh yah.. it turns out that gparted has that ms-sys program so that will work hopefully.

---

### Post by crjackson on 2007-12-27
> **systemintheglitch said:**
> Oh yah.. it turns out that gparted has that ms-sys program so that will work hopefully.

There is a very good chance that MS DOESN"T have built in drivers on the CD for your HD.  It won't install on my SATA WD Drive with a 2 year old MSI motherboard.  I have to use floppies with the SATA drives to continue the install for XP.

You can also download the needed driver and burn them to a CD for loading at installation.  I've not done it myself but as I understand it, many people do.

---

### Post by systemintheglitch on 2007-12-27
Oh well..

I don't think I wanted windows that badly.. It would be more complicated because i don't have a floppy, just an external cdrom drive which is being used by the xp install disk..

I will have to come back to this later.

---

### Post by jimrz on 2007-12-27
If it turns out you really want win back, you can get restore disks from IBM. Not sure what they charge for then these days, though. Also, have you tried your "access ibm" button to see if your oem restore partition is still there and possibly functional? In fact, if grub shows you a boot option some thing like "Windows NT/2000/XP" that would be your restore partition. At least that is what the one on my T42 is called in the grub menu list.

---

### Post by louieb on 2007-12-28
I've got a T30 so I went over to the ThinKPad forum. The basic fix was to check to make sure BIOS is set to compatibility mode,  then boot the XP cd in recovery mode and run fixboot and fix mbr. 
Here a guy in the same situation he got XP install
[http://forum.thinkpads.com/viewtopic.php?t=54034&highlight=install](http://forum.thinkpads.com/viewtopic.php?t=54034&highlight=install)

---

### Post by systemintheglitch on 2007-12-29
> **louieb said:**
> I've got a T30 so I went over to the ThinKPad forum. The basic fix was to check to make sure BIOS is set to compatibility mode,  then boot the XP cd in recovery mode and run fixboot and fix mbr. 
Here a guy in the same situation he got XP install
[http://forum.thinkpads.com/viewtopic.php?t=54034&highlight=install](http://forum.thinkpads.com/viewtopic.php?t=54034&highlight=install)



Way cool man! Thank you!

Would you mind telling me how to boot the xp cd in recovery mode?
And how do i run fixboot and fix mbr? Should there really be a space in fix mbr? i will check that link you gave.

Also, how do you set compatiblility mode in BIOS?

Once again, thanks for your help friend.

---

### Post by systemintheglitch on 2007-12-29
Oh yah..

I don't THINK i can even get to the section where I select the repair option.. 
I get the bluescreen of death right after it loads the ntfs and fat32 CODE and all the initial stuff.. Unless you know of some secret key combination, i am not able to provide ANY input from the keyboard before it crashes.. It doesn't even ask.

---

### Post by alx010 on 2007-12-29
Just did a quick Google on Stop 0x0000007B. Have you checked these 2 pages?

[http://www.windowsfordevices.com/articles/AT6380158626.html](http://www.windowsfordevices.com/articles/AT6380158626.html)

[http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103)

The error is definately driver related. You said that you've tried 2 XP discs. Did either of them come with your machine? XP recovery discs tend to be vendor specific, thus the driver issues.

---

### Post by louieb on 2007-12-29
> **systemintheglitch said:**
> ... Should there really be a space in fix mbr? Also, how do you set compatiblility mode in BIOS? 
I fat fingered fixmbr.   Haven't been in my ThinkPads BIOS so not sure where the compatibility mode switch is.  But thats seem to be the key to getting  the XP CD to work. 
Also IBM/Levono also has a disk call Dr. PC (free download) Might want to take a look at it. 

Also another good place to get information about Linux and ThinkPads is   [ThinkWiki - Linux on ThinkPad]("http://thinkwiki.org/wiki/ThinkWiki")  Good Luck.

---

### Post by julian67 on 2007-12-29
I installed XP for someone several months ago on a Thinkpad with SATA drive...you definitely have to go into the BIOS and set the hard drive to compatibility mode. Then install the MS OS and then install the SATA drivers and then reboot and change the BIOS setting back and it should then boot XP and run the drive as SATA. Of course any GNU/Linux distro's installer will just recognise the SATA drive and just work :lolflag:

---

