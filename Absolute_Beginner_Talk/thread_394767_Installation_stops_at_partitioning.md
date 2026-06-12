---
title: "Installation stops at partitioning"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by hwheller on 2007-03-27
I am trying to install Ubuntu 6.06 on a Dell Optiplex 170L with the live CD.  It is to be a dual boot with Windows XP.  I have defragmented and know that there is at least 20GB of free space on an 80GB hard drive and the disk is less than a quarter full. The live CD works well for general use--Internet, Open office, etc.-- and I have used the menu option to check the CD.  The installation goes fine until it comes to the partitioning section.  I chose the first option--to resize the partitions.  It give me a slider showing 36 GB, 50%.  I reduced this to 20 GB and clicked forward.  It responded that it couldn't make enough space to install.  I reduced the amount to 16 GB.  After i clicked the little disk cursor keeps spinning and after 10 minutes I cancelled.  How long should it take?  Could I use the option to install in the largest space instead of the first option?  The defragmenter I used showed a large free space at the end of the disk.

---

### Post by camz on 2007-03-27
The best method is to manually partition the disc. Click manually partition, then click OK. You will be given a table with partitions and free space. With an empty space, right click and choose to create new partition, move the amount so that you make enough room for whatever you want (NOTE: make sure that the partition you make is format ext3). Make sure to also make partitions for root and swap, 1GB each should be enough to be safe.

If this doesn't work, let me know, I do my best..

---

### Post by hwheller on 2007-03-27
Thanks.  I'll try the manual partition a little later today.

---

### Post by hwheller on 2007-03-27
The manual partitioning didn't work either.  I selected manual partitioning, clicked forward and the disk cursor just sat there.  After 5 minutes I canceled.  It is recognizing the hard drive and it has the size right.

---

### Post by c-breakdown on 2007-03-29
When I right click to add a new partition, the add new partition is grayed out so i can't choose it. Is there something I can do about that?

---

### Post by gigaferz on 2007-03-29
I had the same problem 3 days ago.

I had a linux rescue cd and I creeated the partition for linux BEFORE running the installer, besides the installer was making windows to fix errors at boot.
Once I created the Linux Partition, I booted from the Livecd
Then I had more problems with the installation, it wanted to install to the winxp partition, so to prevent it, I  MOUNTED the windows partition   so it was ignored.

Honestly the usual installation never run. So I did 3 partition with the option in the installer to do it manually.  And if the installer freezes you also have on the live cd gtparted and qparted make them ext3, and/or if you want to share files create for home a fat32- Remember to use sudo for the partition managers
1 or 2 gb for swap
10 for /
and the rest for home
Maybe you could do it with less space for  "/" but you gotta google around to see whats going on.

Hopefully the installer will see your empty partition and  will perform a standard installation so you dont mess around with the "manual" option.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by gigaferz on 2007-03-29
Hey! c-breakdown, right click it and check out the properties, somebody could help you out better with that info.

---

### Post by c-breakdown on 2007-03-29
I'm assuming you mean "Information" since I have no option for properties when I right click.  And the information states the following:

File System: NTFS
Size: 149.05 GiB
Used: 33.63 GiB (23%)
Unused: 115.41 GiB (77%)
Flags: Boot

Path: /dev/hda1
Status:  Not Mounted
First Sector: 63
Last Sector: 312576704
Total Sectors: 312576642

---

### Post by gigaferz on 2007-03-30
Have you tried using qtparted (open a terminal and type sudo qtparted)

to create partitions?

---

### Post by hwheller on 2007-03-30
I've been a few days getting back to this.  I looked around the Internet for more information.  I decided to try partitioning before I installed.  I used the Ubuntu 6.06 Live CD and when it got to the desktop I used the Terminal and typed "sudo gparted".  Gparted started and I got a window with a long list of "error reading inode #8 etc";  then unable to open /dev/hdc read-write ... unrecognized disk label.  I think this is a Lexmark printer that always shows up a mass storage device.  Below was the partitioning table.  It showed
/dev/hda1  fat16  31.35MB  Used 7.23MB     
/dev/hda2 ntfs    75.46Gb   Used 19.86GB
unallotted           15.69MB

I chose had2, chose resize, set hda2 to about 50GB, leaving about 25 free.  When I applied it began, then stopped with "Error while resizing/moving /dev/hda2
I tried again using 60GB and got the same result.

Would it be worth trying a different copy of gparted, e.g. download it from sourceforge or somewhere?

Does anyone have any ideas on how I can repartition?

---

### Post by gigaferz on 2007-03-31
if "qtparted" fails, you could try downloading  "System Rescue Cd" is a gentoo based "live cd.

That is what I used "gparted" gave me many problems.

---

### Post by hwheller on 2007-03-31
Thanks.  I already tried qtparted on the System Recue CD.  I found out that the drive has bad sectors.  That seems to be what is causing the problems.  It looks like I'll have to replace the drive before I can install Ubuntu.

---

### Post by dstew on 2007-03-31
Maybe you can repair the bad sectors. If it is a ntfs, you can use chkdsk /f from the Windows command line.

---

### Post by Sabar on 2007-03-31
I also had this problem. But I never could figure it out so what i did was put an old hard drive in my computer that I had laying around. Let the live CD do a full re-format on it. then did the full installation. Works fine that way

Two things I wondered about were if I had bad parts to my Hard Drive or, one thing I noticed when I ran a disk De-frag was that there was blue ( data ) on both ends of my graph. Now I don't know if this is a literal or just a theoretical  graph. I was wondering if maybe the reason it couldn't partition the hard drive was because there was data on both ends of the disk?

Sorry I am no help just wanted to let you know there is some one else out here who feels your pain.

Sabar
:confused:

---

### Post by hwheller on 2007-04-01
I did do error checking from the "Drive C"- Properties-Tools and I selected the fix option.  That appears to be the same as running chkdsk from command line with /f.  It finished up and when I found the log it showed that there were bad sectors, but it didn't say anything about fixing them.  I might try running it again.  Some people seem to have needed to run it several times to get a problem fixed.  

My defrags worked fine.  They showed all the files at one end and a lot of free space at the other.

I'll try checking the disk again and try to fix it.  then I'll try a new hard drive.

---

