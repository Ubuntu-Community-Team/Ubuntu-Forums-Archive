---
title: "Cannot partition HD - &quot;Error resizing /dev/hda1&quot;"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by sunv on 2007-07-07
I have Ubuntu live CD 6.06 and i've been trying to install it on my system which is a HP dv1000 laptop (1.86 Ghz, 1 GB ram, and 100 GB HD)

So far Windows XP takes up basically the whole hard drive.  I put in the live CD, click on install, and went all the way to partitioning space for Linux and I manually partitioned it to shrink the NTFS windows partition by 20 GB to allow 20 GB for the linux OS.

When I tell GParted to do the job, to shrink the NTFS partition, it says "Error resizing /dev/hda1" or something like that.  I tried making the NTFS partition 30GB less and even only 10 GB less.  Sometimes it just sits there, frozen, or sometimes it just gives me the error.  I went back to windows and defragged the HD, and went back to linux to shrink the partition but it still gives me the error.

What is the problem here?
With these errors and frozen apps, its already giving me a dreading look into linux.

---

### Post by bren on 2007-07-07
try defragging once more in windows.

then if you can bother, download the alternate install cd.     this has less graphic interface but same process to install.   make sure you burn at the slowest speed and check the cd before installing.


i would also recommend you choose 7.04 unless special reason to stick with 6

bren

---

### Post by Skidpad on 2007-07-07
Since you are attempting a laptop installation, read [**THIS**]("http://www.linuxdevcenter.com/lpt/a/6554") as well.  This is what I had to do to get mine going (even though I did not have an error message - mine just hung during the install).

---

### Post by sunv on 2007-07-10
Im a little confused on what the FAT32 partition is used for?
Is it drive space that is used by both windows and linux?  does that mean you can grab windows files from there and run them in linux, and linux files and run as windows? (ie mp3s, movies)

What if you plan to keep the two OSes completely separate, as in windows programs only in NTFS and linux only in ext3?  Can I not have a FAT32 partition?

When i defrag, I notice there are some green lines on the wayyyy right side of the picture of my drive.  Those are unmovable files and I dont know how to move them to the left side.  I am guessing why I am getting errors and why my installation hangs.  Any idea how to move those unmovable files?
CHKDSK?  I ran it and it detected errors but couldn't fix them because my HD was being used.  So next restart it will fix it.

Feedback and advice is appreciated.  Thanks guys!:)

---

### Post by karmakaze11 on 2007-07-10
Try using [Partition Logic]("http://partitionlogic.org.uk/") to partition your HDD; I was having the same problem, but PL solved it for me, no problem. There should be instructions on the page, but it works in a similar way to the Live CD - you have to save the iso to CD as an image, and boot into it.

---

### Post by bigken on 2007-07-10
download and burn the gparted liveCD this will sort you partitions for you

---

### Post by sunv on 2007-07-10
Will Partition Magic or gparted liveCD be able to move the unmovable files?

---

### Post by Ek0nomik on 2007-07-10
> **sunv said:**
> Im a little confused on what the FAT32 partition is used for?
Is it drive space that is used by both windows and linux?  does that mean you can grab windows files from there and run them in linux, and linux files and run as windows? (ie mp3s, movies)

What if you plan to keep the two OSes completely separate, as in windows programs only in NTFS and linux only in ext3?  Can I not have a FAT32 partition?

When i defrag, I notice there are some green lines on the wayyyy right side of the picture of my drive.  Those are unmovable files and I dont know how to move them to the left side.  I am guessing why I am getting errors and why my installation hangs.  Any idea how to move those unmovable files?
CHKDSK?  I ran it and it detected errors but couldn't fix them because my HD was being used.  So next restart it will fix it.

Feedback and advice is appreciated.  Thanks guys!:)

You hit it on the button.  The FAT32 partition is for sharing files between Linux and Windows.  FAT32 is your safest option to sharing between the two operating systems, because FAT32 is natively read by both operating system.  You can get Linux to read NTFS, just as you can get Windows to read EXT3, but FAT32 is the safest option, as the other two aren't fully supported.

Music, movies, images, etc should be put onto the FAT32.

You cannot, however, share programs as you were talking about, because software is used entirely different by both operating system.  For an examle, you can't use Thunderbird installed on Windows in Linux.  You will need Thunderbird installed twice, one for Windows, and one for Linux.  Software won't function the same in both operating systems, that is where some fundamental differences come into play.  Another example would be the instant messenger Gaim (now called Pidgin).  You can't use the Gaim version from Windows on Linux, so putting it on the FAT32 won't matter.  You have to have it on Linux and Windows.  So the note to take out of this, is install software on the respective drive (EXT3 or NTFS), while things that can be shared such as text documents, music, movies, etc, can go on the FAT32.

---

### Post by Skidpad on 2007-07-10
> **sunv said:**
> Will Partition Magic or gparted liveCD be able to move the unmovable files?
*Read the link I posted earlier*...it is your pagefile and hibernation file causing your problem, and yes, they are movable.

A quote from the linked page: **"One problem you may encounter in defragmenting a Windows disk using the Windows Defragmenter is "unmovable files" (the green bars) located in inconvenient locations (on the right side of the display, near the end of your disk). The two most common unmovable laptop files are the Windows operating system paging file (pagefile.sys) and the hibernation file (hiberfil.sys), which stores the system state when the XP operating system goes into "hibernate" mode. An easy solution is to temporarily remove these files, then reinstall them after you've resized the NTFS partition."**

---

### Post by sunv on 2007-07-13
ok I defragged and made the paging file size to 0 and turned off "enable hibernation" and the unmovable green files went away.
Now if I leave the paging file at 0 and hibernation disabled, if I restart the system and install Ubuntu with its partition taking up the butt-end of the drive, when I enable paging file and hibernation in Windows again will it be able to make the hibernation and paging file?  Because now those unmovable files cannot be placed in the ext3 linux, so does Windows just make space for them in its own partition, unrelative to its physical space on the platters?

This is what I mean:
When I disable hibernation and paging file, my HDD is shown as all blue crammed to the front and 50% free, which is ideal for making partitions.  But after enabling hibernation and pagingfile, those green bars appear on the far butt-end of the HDD again.  So its logical to create partitions and install ubuntu when those unmovable files aren't there, but im hoping there wont be problems later when Windows tries to create them in an area of the HDD that is sectioned off.
So im wondering will this cause problems?

---

