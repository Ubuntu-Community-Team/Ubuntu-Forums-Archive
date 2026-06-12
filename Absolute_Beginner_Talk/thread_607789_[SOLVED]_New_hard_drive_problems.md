---
title: "[SOLVED] New hard drive problems"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Znort_Ubern00b on 2007-11-09
Have just put new sata hard drive in my machine...however when i did 
sudo fdisk -l i get this message:

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9964    80035798+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    5  Extended
/dev/sdb5               1         243     1951834+  82  Linux swap / Solaris
/dev/sdb6             244       30401   242244103+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdc doesn't contain a valid partition table


how do i ensure /dev/sdc has a valid partition table???

---

### Post by bcrom on 2007-11-09
use sudo apt-get install gparted to install the gnome partition editor.  Select your drive and then format it using a supported filesystem.

---

### Post by Pumalite on 2007-11-09
Better use Gparted Live CD (drives are not mounted)[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by Dr Small on 2007-11-09
> **Pumalite said:**
> Better use Gparted Live CD (drives are not mounted)[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
+1
Agreed.
You don't want to reformat drives while mounted on that drive... Well, you can't ;)

---

### Post by az on 2007-11-09
You can run gparted from your Ubuntu install.  The drive is brand new and doesn't have a partition table on it yet.  This is normal.

You don't need to run a partitioner from a live CD in this case.  You only need to do that when you want to partition a drive you are running from.  You are certainly not using this drive yet.

---

### Post by Znort_Ubern00b on 2007-11-09
ok, have got gnome part editor...am real new to this...what do i do from here??which filesystem would be best?

---

### Post by Pumalite on 2007-11-09
It's better to partition hard drives while unmounted.

---

### Post by bcrom on 2007-11-09
Since this is not your primary drive (the drive from which you're running an OS) you can use gparted from inside ubuntu.  You don't need a live CD.

If you're only going to use the drive in ubuntu, go ahead and format using the ext3 filesystem.  I think it's a little more error-proof than other filesystems.  However, if you want to use this drive with windows too, use either FAT32 or NTFS.  If use use NTFS you'll need the NTFS read/write drivers. 

To get ntfs read/write driver do a 

sudo apt-get install ntfs-3g 
and 
sudo apt-get install ntfs-config

then go to Applications->System Tools->NTFS Configuration tool and check all available boxes.

---

### Post by Znort_Ubern00b on 2007-11-10
can i partition so about 200gb is for windows(with 20gb for os) and the rest is for linux???

so i have 
pt 1 os 20gb xp pro
pt 2 windows file storage 180gb
pt3 linux file storage 300gb

---

### Post by Harpoon on 2007-11-10
The simple answer is "yes, of course."  It's your drive and if the amount of space you want to assign to those partitions seems right to you, linux will have no objection.

If you are running Feisty or Gutsy, you don't need to worry wabout ntfs-3g as it is installed by default.  You may need to download and install (and then run) ntfs-config, however, if you want to automatically mount the usb ntfs partitions as read/rwite in ubuntu.

No need to reboot to a cd to partition (in your case), just

gksu gparted

and off you go.

Be aware that when you do partition the drive, "root" will own it.  You might want to

sudo chown -R username:username /media/<disk>

 to give ownership to yourself.

---

### Post by Duck2006 on 2007-11-10
> **Pumalite said:**
> It's better to partition hard drives while unmounted.

+1

---

### Post by Othyz on 2007-11-10
> **Harpoon said:**
> 

Be aware that when you do partition the drive, "root" will own it.  You might want to

sudo chown -R username:username /media/<disk>

 to give ownership to yourself.

I seem to be having a similar problem. I cannot write to drives and I cannot change permissions.  For added excitement one of my drives dissappears.  Any thoughts?

This noob would be grateful.

---

### Post by Pumalite on 2007-11-10
Get Knoppix Live CD:[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
And boot from it. Tell us what you see.

---

### Post by Othyz on 2007-11-10
> **Pumalite said:**
> Get Knoppix Live CD:[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
And boot from it. Tell us what you see.

Same thing.  Can not change read/write permission.  Plus says all drives are 708 bytes.  I have 2 @ 250 G , 1 @ 500 G and Ubuntu is located on a 20G. 

Whats the point in having a terabyte if you can use it! :biggrin:

---

### Post by Pumalite on 2007-11-10
I'd get into the BIOS and check IDE Configuration (or SATA)

---

### Post by Othyz on 2007-11-10
... forgot to say that I used Gparted to format 2 of the drives into ext3.  One of the 250G's is still ntfs, since it still has 230G of MP3's on it.  I am trying to get this all backup on a more stable system like linux.  Real tired of MS.

---

### Post by Othyz on 2007-11-10
> **Pumalite said:**
> I'd get into the BIOS and check IDE Configuration (or SATA)

I have a Gigabyte GA-7VAXP

IDE1 - 20G master, 500G Slave
IDE2 - DVD ROM master, CD-RW slave
IDE3 - 250G master, 250G slave

When booting it only recognizes IDE1&2 (primary master/slave & secondary master/slave) I don't think my CD & dvd fire up if they are on IDE 3

The setup instructions said to put the CD's on IDE2.  Does this not bode well in Linux enviroment?

---

### Post by Pumalite on 2007-11-10
DVD as 2nd master is fine. Set it to 'Auto' or 'AHCI' on BIOS

---

### Post by Othyz on 2007-11-10
I have it set to auto detect in primary/secondary area of BIOS. I do not see an AHCI anywhere.  Do you think the onboard RAID chip is messing me up?  I have that set to ATA.  So that should be fine.

I just noticed that Ubuntu thinks my drives are scsi connection.  They are ATA, weird.

---

### Post by Pumalite on 2007-11-10
Since Feisty, drives are sda, sdb, etc

---

### Post by Othyz on 2007-11-10
> **Pumalite said:**
> Since Feisty, drives are sda, sdb, etc

Ah...Bach... Then all is Ok there.  

Ownership on drive changes when mounted or unmounted.  when mount and go into properties i can see owner go from "unknown" to Root

Shouldn't I be the owner?

---

### Post by Pumalite on 2007-11-10
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://ubuntuforums.org/showthread.php?t=589909](http://ubuntuforums.org/showthread.php?t=589909)

---

### Post by ScarfaceIII on 2007-11-10
of course Gparted is the easiest solution, since it has a GUI, but I read you use fdisk, so why not use that?
I bought a SATA HD today And had the same question? How to install this brand new baby?
You answered my question, because I completely forgot about 'fdisk -l', which displays the '/dev/XXX' of the new HD. Since you have that, now it's easy! You can
sudo fdisk /dev/sdb
them digit 'm' at the prompt to know what the commands are for fdisk and build a new partition table and then do what you want with your Hard Disk ;)
enjoy!

---

### Post by Othyz on 2007-11-10
Thanks Scar, but no help there.  I already Gparted the drive anyways. 

I am searching in vain for the darn thread I had seen that explained how to give me ownership of those drives.  Something about chmod I think.  I'm just looking for the command line that gives me read write permission for my drives.  

I hate being the new guy.  Fortunately I like "free", (as long as I don't count the hours spent learning :) ) , sercure and the idea of a stable platform.  So I'm willing to put in the time like I'm sure you all did in the beggining.

Thanks to you too Puma.  BTW, the first link links did not take me anywhere if they were suppose to, no joy.

---

### Post by Pumalite on 2007-11-10
Did the second help?.

---

### Post by Othyz on 2007-11-10
OMG! I'm an flipping IDOIT!!!  

OK, here we go. (I just might make a sticky outta this for other noobs)

I used 'gksudo nautilus' in terminal - but did not see how it was helpful.  Not until I MOUNTED the drives in question.  So mount drive THEN ***'gksudo nautilus***'  Then double click File system.Go to the folder marked "media".  There you find your drives - right click - properties - permission tab.  Now you can change owner.  

I got it!!!  Thanks for hanging in there with me Pumalite!!

...now if I can just get my windows machine to acknowledge the Linux box I can start backing up data.  But that my friends will be for another thread!

Thanks all, see you around campus.

---

### Post by Othyz on 2007-11-10
Should this thread be marked solved? If so, by me or is that a moderators thing, let me know.

---

### Post by Pumalite on 2007-11-10
Mark it solved, but here is the driver you need in Windows:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

