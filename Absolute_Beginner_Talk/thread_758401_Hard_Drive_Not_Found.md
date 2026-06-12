---
title: "Hard Drive Not Found"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by sourcepro on 2008-04-18
I'm attempting to install Ubuntu 7.10 onto a Compaq DeskPro (P3 800) with a Western Digital 40 gig hard drive (internal).

Everything runs great from the LiveCD, but if I attempt to install to the hard drive, it can't find ANY hard drives.

From the command prompt, running:
sudo fdisk -l 
returns nothing at all.

The hard drive is a clean drive with no existing FAT or NTFS partitions at all.

Any suggestions?  

Thanks

---

### Post by sourcepro on 2008-04-18
By the way, the BIOS recognizes the hard drive (when I boot into the bios setup utility).

It was an older machine that was running Win2K... All I did was fdisk and remove all existing partitions, then boot the LiveCD (so in other words, the hard drive that Gparted can't see was working 10 minutes before I booted to Ubuntu)  All that being said, I don't believe the issue is the hard drive itself.

---

### Post by ramjet_1953 on 2008-04-18
Try downloading the gParted Live CD iso image and burn it to a CD.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Then boot your system from this CD and see if you can partition your HDD to a single ext-3 partition.

Then try booting up with the Ubuntu CD and see if you can install.

Good Luck!

Regards,
Roger :cool:

---

### Post by bumanie on 2008-04-18
You will need to format the hard drive to ext3 so that a file system exists on it. At present it is a raw disc and an OS won't install unless a file system is present. You can use gparted off the live ubuntu cd or burn a dedicated gparted live cd to this.

---

### Post by sourcepro on 2008-04-18
I downloaded the GParted LiveCD and booted with it.

It recognized the hard drive and I partitioned a single EXT3 partition.

Then I shutdown and booted using the Ubuntu LiveCD and it still does not see the hard drive.

Any other suggestions?

Thanks!

---

### Post by bumanie on 2008-04-18
How do you mean the live cd doesn't see the hard drive? What exactly happens? Does the live cd work, as in run the operating system? Have tried installing, what happens at the partitioning stage or does the cd not ru at all? If gparted sees the hard drive and can format it, I can't see why the live cd would not work unless there is something wrong with it, such disc errors or md5 checksum does not  match.

---

### Post by sourcepro on 2008-04-18
As I mentioned in my original post, Ubuntu runs fine from the LiveCD.

If I choose to install it, I enter some time zone info, etc, then it launches GParted (to determin which partition to install to) and there are NO devices found (as if my system doesn't have a hard drive attached at all).

I guess Microsoft didn't corner the market on having problems with their OS.  :-)

---

### Post by bumanie on 2008-04-18
I have never heard of that before, however there is an alternate install cd which is text based and often works when the live cd won't. I can only guess that it is some sort of hardware conflict (not that uncommon), which the text based installer usually gets around. Go to the ubuntu main [site]("http://www.ubuntu.com/getubuntu/download") and check the box under "start download" The other thing you could do is check the cd for errors and do an md5checksum to make sure the download was not corrupted in some manner.

---

### Post by sourcepro on 2008-04-18
I'll try the text-based version this evening.

However, I'm confident the LiveCD I'm using is fine, since everything runs great as long as I run from the CD and don't try to install it.

That being the case (and since the GParted LiveCD DID detect my hard drive), I think it is a driver issue for sure.

Thanks,

Patric

---

### Post by sourcepro on 2008-04-19
Ok, same problem with the Alternate CD.....

To recap, I can run just fine from LiveCD....

But if I try to install or run Gparted from the LiveCD, it can't detect my hard drive.

If I run the alternate (text) install, same problem (can see the hard drive).  I tried every driver listed and still no luck.

Per someone's suggestion, I downloaded Gparted separately and burned that ISO to a CD, booted to it, and I COULD see the hard drive (and partitioned it to EXT-3).  However, if I boot to either the Ubuntu LiveCD or Alternate (Text Only) CD, neither can detect my hard drive.

Any other suggestions?  I think I've had my fill... Windows 2000 or XP are looking mighty fine right now... Perhaps my gut instict was right... Ubuntu is more hype than anything else (if you're working with older hardware, anyway)  lol

---

### Post by sourcepro on 2008-04-19
In case anyone else has this problem, I finally was able to fix it.

I changed the jumper on the Western Digital hard drive from Master to Cable Select and it worked fine.

---

### Post by tomwilsonfl on 2008-04-23
Praise God for your recent thread. This was exactly the same problem I was having with my old Compaq Deskpro. It isn't specific to Ubuntu either. I was experiencing this problem installing Linux period.

I have a Western Digital 80 GB drive, brand new. When I switched it to Cable Select everything started clicking!

Cheers!

Tom :)

---

### Post by absheva on 2008-04-27
Your solution of cable select was the lead I needed.  I also was trying to dual boot a Compaq deskpro.  It started as having one hard disk and one cd each on it's own ide cable.  I tried various combinations, second drive as slave on primary IDE; second drive as master on secondary ide; second drive as only device on secondary.  In all these scenarios WinXP saw the disk and could access it but not Ubuntu install.  I tried formatting it with different file systems but nothing worked.
When I saw the tip of channel select I tried it.  I still had to play a bit.  The first drive is oversized, (250g) and when I switched it to cable select it the computer did not see it correctly.  I now have the original disk and the cd on the primary ide as master/slave.  The second drive with ubuntu is channel select on the second ide.
Thank you very much.

---

