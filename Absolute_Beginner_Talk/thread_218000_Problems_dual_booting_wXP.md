---
title: "Problems dual booting w/XP"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Handyman's Special on 2006-07-18
Hello,

Twice I have tried running XP & Ubuntu from different partitions. I carefully made a Linux SWAP partition & one for the system, leaving XP on the 1st one.

Each time the grub writes itself to the MasterBootRecord, XP will not open. 

I have a dual boot with XP & win2000. It seems I may be forced to simply run Ubuntu from the Live-CD indefinetely. 

Has anyone else had this problem?

Regards,
Handyman's Special

---

### Post by GuitarHero on 2006-07-18
You have to edit your grub menu file to add Win XP into it, then it will appear on the boot list when you start up.  If you need to erase ubuntu and restore your master boot record, you need a thing called fdisk.  Boot with that on a cd and you can fix your mbr with that, google for it.

---

### Post by nowadays who knows on 2006-07-18
OK are you booting xp , win 2000 and UBUNTU or is win 2000 a typo???
It matters to determine if you are wanting to boot load with grub or microsoft's ntloader.

---

### Post by molly_001 on 2006-07-18
To Handyman --

I feel your pain.  The first time I tried to install Ubuntu into its own partition (plus a Swap partition) I had the same issues.  (Yes, even after editing GRUB, and learning a BUNCH about GRUB along the way.)  The truth is that the Ubuntu 6.06 LiveCD install routine just doesn't work some of the time.  Based on watching a couple of thousand posts, it seems that it just plain won't work for about 10% of folks unless they start fresh (as I did).  Here is the plan that worked for me after my initial frustrations, and which has subsequently worked on two other dual boot machines:

<items 1 and 2 are interchangeable, depending on whether you have succeeded to boot into your XP installation by the time you read this>

<Download and burn the .iso image of the ***Alternate Install Cd*** for Ubuntu 6.06 before moving on>

(1)  Save 100% of the data you wish to keep from that XP installation.  Save it onto another hard drive, or burn it to optical media, etc.
(2)  Use your Windows install CD to reformat and reinstall Windows on the drive.  Delete any and all old partitions.  Let this new install of Windows occupy 100% of the drive space.  So you will have a single ntfs partition covering the entire drive.
(3)  Install your basic stuff to Windows - get Microsoft updates, put on basic software.  Then defrag.  Then defrag again.
(4)  Use the Ubuntu LiveCD only to access GParted -- a partition utility.  Use GParted to resize that ntfs partition (make it smaller) to the new and smaller size you desire.
(5)  After you have shrunk Windows partition, just leave the rest as unpartitioned space (unformatted for now).
(6)  Then boot your machine using that Alternate Install CD.  Use the text mode installation according to the instruction page below, and you will have your dual boot in no time:
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

And of course, any questions, just ask!

---

### Post by Sef on 2006-07-18
How did you do the install: with the livecd or the alternate install cd?

If you have used the livecd, download and burn the alternate one and dual boot that way.  There have been problems with the livecd at times, so perhaps this will take care of your problem without having to reinstall XP.

Herman's site is an excellent one for [dual booting]("http://users.bigpond.net.au/hermanzone/").

---

### Post by molly_001 on 2006-07-18
To Handyman --
Sef is correct, it is a good idea to TRY installing via the Alternate Install CD before reformat of drive.  However, just make sure you are comfortable with all your previous data being backed up.  If it's not backed up, you may wish to do the (boot using Win Xp CD -> Recovery Console option --> fixmbr command) as described above.

---

### Post by Handyman's Special on 2006-07-18
Thank you all for the excellend advice.

I felt more confident after reading that and installed Ubuntu.

I am able to enter both of the Windows installations (XP & W2K) and Ubuntu.

Now it is time to set down and learn all I can about operating with Ubuntu. I am so bummed out by Windows Genuine Advantage. Why did I spend the money to buy a copy of XP. Obviously I do not OWN it. My biggest regret is the wonderful game I was Beta Testing will only operate in the Windows environment. Oh, well. . .

More questions to come,
regards,
Handyman's Special

---

