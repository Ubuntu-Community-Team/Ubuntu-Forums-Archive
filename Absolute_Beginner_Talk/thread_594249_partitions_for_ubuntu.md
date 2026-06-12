---
title: "partitions for ubuntu"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by aeonwings on 2007-10-27
I currently have ubuntu installed on my system but I didn't give it enough space, so I would like to add more disk space. Because of this I want to delete the partitions, root and swap, and have windows, NTFS, to reclaim that space back. And then I want to shrink windows partition down even further, and create a new partition to install ubuntu in, just much larger. 

Last time I when installing ubuntu, I let the program auto partition for me, but this time I would like to use the "manual" option, and choose how big the partitions should be. My question is....do I need any special commands or instructions to create a root and swap partitions, like make it a boot partition or something? 

I will be using the Gparted LiveCD to delete the current ubuntu partition, and expand the windows partition. Then I will use Ubuntu LiveCD to make new, bigger partition for Ubuntu. Any advise would be really helpful.

---

### Post by genbuntu on 2007-10-27
Try reading this, it may help:

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by DezSP on 2007-10-27
Linux partitions are much more flexible than NTFS, though, I suppose, in context they're equally resizable. Anyway, you shouldn't need to reinstall anything to do this, simply shrink your NTFS drive, then expand the ext3 ones to fill up the empty space.

Though I'm sure you're aware of the dangers, do always be careful when resizing NTFS drives...

---

### Post by trak87 on 2007-10-27
Sounds like a good plan. Have backups or be very careful not to delete the wrong partitions (if applicable). You just need to define the partitions. The installer will determine which partition to boot based on where /boot is installed, but yes, you do need to create all the partitions and the swap partition using the manual option. I generally do something like this:

ntfs partition for windows (10 gig?)
/   (root 6-8 gig)
/boot  (200 meg)
/home (4 gig)
swap (twice the size of RAM)
/media/extra

You didn't mention a home partition, but having one will become very important when you install the next version of Ubuntu. Very recommended. The boot partition isn't really necessary, but I create one sometimes. The /media/extra directory is for the leftover space. If you don't need this, just make your /home directory bigger.

---

### Post by aeonwings on 2007-10-27
> **trak87 said:**
> Sounds like a good plan. Have backups or be very careful not to delete the wrong partitions (if applicable). You just need to define the partitions. The installer will determine which partition to boot based on where /boot is installed, but yes, you do need to create all the partitions and the swap partition using the manual option. I generally do something like this:

ntfs partition for windows (10 gig?)
/   (root 6-8 gig)
/boot  (100 meg)
/home (4 gig)
swap (twice the size of RAM)
/media/extra

You didn't mention a home partition, but having one will become very important when you install the next version of Ubuntu. Very recommended. The boot partition isn't really necessary, but I create one sometimes. The /media/extra directory is for the leftover space. If you don't need this, just make your /home directory bigger.



Ok so....you're suggesting that I should create a total of 3 partitions, excluding the NTFS of course. So a / (root), a /home, and a swap? shouldn't the "/home" partition be biggest??? since it will hold all the files? or maybe I misunderstood something. I have 50gb of space to use for all the partitions beside the Windows partition. Maybe:
/ (10gb)
/home (38gb)
/swap (2gb)

---

### Post by pdlethbridge on 2007-10-27
10 gig for the home folder will be fine

---

### Post by aeonwings on 2007-10-28
Ok I just thought of something. Since Windows can't read files in /home partition or any ext3 partition for that matter, wouldn't it make more sense to save files, mp3, videos and so on, to Windows partition(My Documents folder) because Ubuntu can read them anyway? I don't know if I'll be deleting Windows any time soon so I was just thinking. 

I guess if I make my /home partition 10gb, then I'll have to save most of my files through Windows partition then.


Oh 1 more thing. Do I need to edit or re-install GRUB again? wouldn't the installer do that for me automatically?

---

### Post by DezSP on 2007-10-28
The installer will re-do GRUB for you.

Make your home partition as big as you like. Then google "ext3 drivers" to find out how you can access it from Windows.

---

### Post by trak87 on 2007-10-28
> **aeonwings said:**
> Ok so....you're suggesting that I should create a total of 3 partitions, excluding the NTFS of course. So a / (root), a /home, and a swap? shouldn't the "/home" partition be biggest??? since it will hold all the files?
/ (10gb)
/home (38gb)
/swap (2gb)

You got it! That looks good. You'll appreciate having the /home directory someday soon.

---

### Post by tdmoore on 2007-11-06
I need assistance and badly.

Here is what I attempted (I admit fully that I got impatient and tried things beyond my skill level).

Running Gutsy on dual boot machine (Windows XP) and tried to do a fresh install after some problems.  When loading I thought that it would overwrite the partitions however when the boot screen came up I now had 6-8 options with 1 being Windows.

Saw this post and tried to clean up the partitions issue through Gutsy using Partition Manager, however my wireless card is a Linksys WUSB54G v1 and is not supported (I know this from trying to get it working with the help of a great Ubuntu person Atreus12) so could not load it.

Then booted into Windows and went to disk management and deleted blank partition and it deleted fine.  Tried second and received an error message and so thought, reboot.(can't remember message, sorry).

Here's where I stand now.  Tried rebooting as mentioned earlier and received this:
GRUB Loading stage1.5
GRUB loading, please wait...
Error 17

Cannot get into Windows either.

Question is: how hooped am I?  

Then, how do I fix this problem without having to reload everything?

I do have Live CD and although  desktop running wireless I can set it up with a hard wired connection, but not sure how to reset the partitions in Gutsy so that it boots properly with Windows as an option.

To the community: I love what I have seen so far and the assistance I have received so far as a newb has been incredible.  Sure hope you can help me out 1 more time....

Thanks....

---

### Post by mike555 on 2007-11-06
Sounds like Winblows messed up Grub , you may need to reinstall Ubuntu , unless someone else has a better idea , maybe booting Ubuntu into repair mode?

---

### Post by tdmoore on 2007-11-06
Have received advice ranging (privately) from using Windows repair of MBR to trying to use Live CD to fix grub...didn't work BTW as I guess I deleted the partition.

Have now gone to our IT team to assist.

Please consider this solved for now.

Thanks....

---

### Post by DezSP on 2007-11-08
You deleted the partition with GRUB installed on it, so the MBR can't work out what to do. Re-installing Ubuntu now should fix it, or you can run Window's fixmbr utility to put it back to a Windows-only machine.

---

