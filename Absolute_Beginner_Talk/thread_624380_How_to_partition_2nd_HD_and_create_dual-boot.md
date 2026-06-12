---
title: "How to partition 2nd HD and create dual-boot"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by mac.stlcards on 2007-11-26
Hi all,

I have just consolidated form 2 computers to one and now I have 2 hard drives.  The first hard drive is windows only and is my wife's main machine's hard drive.  The 2nd hard drive is newly formatted (windows only allowed me to do NTFS) ~250gigs.  My wish is to partition the 2nd drive so I have about 150gigs to use for windows still (so my wife can continue to make videos of our 1 year old son) and then have 100gigs for Ubuntu.  

I did my best to search for items regarding this, but I'm too new to really know what I'm looking for in some threads.  I read about multiple partitions for /home and others, but I'm not sure how to do this either.  Once I figure out the partitions, how do I go about creating a dual boot.  It should be easier since Windows is already installed.

Please let me know if I need to provide any other information, and feel free to point me to guides.  I may need a little hand holding since this will be my first install ever.

Thanks in advance!

---

### Post by Afkpuz on 2007-11-27
I was a little confused by what your exact situation is.  I'm assuming that

1.) This 250 GB hard drive is the only hard drive in your comp.  If you have more than one, these instructions don't apply completely.

2.)  That windows is already installed on this hard drive already.  

[U]
So, to set up the 250GB for stand alone (no other hard drives) dual boot, do this[/U]






First off, download this.

[http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-10.iso?modtime=1194289031&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-10.iso?modtime=1194289031&big_mirror=0)

This is the latest version (as of 11-05-2007) of a program called "gParted".  That's your partitioner.  Burn that image to a cd, and then get your self a copy of ubuntu.  

To save yourself from some potential headaches, I recommend using an ALTERNATE INSTALL DISC.  You can get them on the ubuntu main download page.  The "live cd" discs boot up a small version of linux from the CD that you can goof around in, and then lets you install ubuntu to your hdd from there.  The alternate is a straight up text installer that bypasses that.  

Ok, so here's what you do.

**To partition your hard drive:**
1.) Make sure your hard drive is plugged in and alive.  (I.E. it's physically hooked up correctly)
2.) Back up any important data just in case 
3.) Defrag your hard drive.  This moves data to the beginning of the drive
4.) Pop in that gParted CD and reboot.  It should boot from the CD.  
5.) Pick the "automatic setup".  I thinks it's the first choice
6.) Follow the prompts about keyboard layout etc.

**Once in the gParted program itself**

1.) click the drop down box near top right and select your desired harddrive.  Check size to be sure.  (You can use gParted to format and partition usb drives too)
2.) If I understand your post correctly, your 250 GB HDD should only have 1 partition.  It might have one puny left over partition (like 8 megs).  Sometimes windows does that.  Select the big main partition and click "Resize/move"
3.) Click on the right arrow next to the bar and drag to the left.
4.) Numbers should start changing and you want to look at "space after partition".  Thats MB  So, you say you want a 150gb for windows and 100 GB partition for linux?  Drag that bar left until "space after" reads approx 100 gb.  Note: you should not grab the left arrow at all.  You want windows to stay at the very beginning of your HDD.
5.) Click "Apply"     Note: this step can take a while.  Be patient and don't cancel this operation!  You might lose all your data!  If this step fails, don't panic.  You need to go back to windows and do another defrag or you forgot to do one at all.  I once had to do 2 defrags to get this step to work.  
6.) If that finishes, you have just partitioned your hard drive!  You should see now 2 parts to your hard drive.  1 that is about 150 gb and another that says something like 100 Gb of  "Unallocated space".  Thats good.

**Ok, now, time to install Ubuntu.**
1.) Exit gParted if you haven't already
2.) Put in ubuntu alternate install disc and reboot
3.) pick "Install in text mode"
4.) Follow on screen instructions until you get to the partition manager
5.) Pick the option "Guided-use largest continuous space" 
6.) That should use that "Unallocated space" and make 2 nice partitions for you.  One for your file system and one for whats called a "swap" area.  This is good.  
7.) Continue following instructions until it asks to install the master boot loader to some place.  Say "NO"!
8.) It will then ask you where to install the bootloader.  In general, you always want to install it on the partition that linux is on.  In your case, it's the second partition.  So, tell it that.  If you have no other hard drives or partitions, enter this as the location: "(hd0,1)"
That means you 1st hard drive on the second partition.  They start counting at 0, not 1.  So put the bootloader on the partition that linux is on.  
9.) You're done!  If any part of the ubuntu installation fails, don't freak out.  Just reboot and try again.  


So to recap, you use gParted to partition your hard drive.  You leave unpartitioned space for linux to use, then use the ubuntu guided installer to "use largest continuous free space".  Then, install the bootloader on the partition that linux sits on.  Does that makes sense?  Now, when you boot up, you get to choose windows or ubuntu.  When booting, ubuntu will load by default after 9 seconds.  Windows will be at the bottom.  

Once again, if you have another hard drive, the instructions change slightly, so let me know if that's the case.  Hope this helps

---

### Post by mac.stlcards on 2007-11-27
Afkpuz, thanks for the excellent info!

I do have 2 hard drives.  The first is only 80gigs and is windows only.  The 2nd hard drive is the one that is 250gigs.  I just want to split it so windows still has plenty of disk space to save to, while putting ubuntu on the remaining space.  Since windows is on the first drive, I don't know the numbering format (hd 0,2?) and I'm not sure how to create the dual boot option.

Also, is it a problem that the disk is formateed in NTFS?  I read that FAT32 was the best, but I'm not sure how to change it.

---

### Post by Afkpuz on 2007-11-27
NFTS won't matter if you use gParted.  It will keep the first part of your hdd as NFTS and leave the 2nd part as unpartitioned space.  Then, the ubuntu installer will partition and format that space during the install.  Thats the "guided-use largest continuous space" thing.  Fat32 can be read by both windows and linux, but ubuntu defaults to ext3 during the partitioning process.  Just use the guided partitioning option of "use largest continuous space".

Since you have 2 drives, make sure that you always are dealing with the correct drive in gParted and the ubuntu installer.  In gParted, theres a drop down arrow in the top right where you can select the correct hard drive.  In the ubuntu installer, it will ask you which drive to work with.

As for the bootloader, I'm pretty sure that you should be able to simply install the bootloader to the master bootrecord.  So, when it asks you if you want to do that, say yes.  In my previous instructions, I had you say no.  Then you wont have to worry about numbering.  Disregard #s 7 and 8 in the installing ubuntu section.  Just say yes to it's prompt about installing to the master boot record.


 So, to set up a dual boot system, Partition that 2nd hdd, install ubuntu on it, and install ubuntu's bootloader to the master boot record.

---

