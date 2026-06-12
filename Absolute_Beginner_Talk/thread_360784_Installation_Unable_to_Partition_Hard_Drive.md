---
title: "Installation Unable to Partition Hard Drive"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by dtholen on 2007-02-13
Please, I could really use some help here. I have attempted an Edgy install several times and the install program hangs at the point to partition my hard drive. I have an XP machine with an 80GB hard drive with 50% free space. I attempted both the automatic and manual options to format. It is important to preserve the XP operating system and many important programs that I use when setting up a dual boot environment. 

It was suggested that I use another install CD burned at a slower speed. I did without success. It was suggested that I try to install Dapper. I did and the installation program hangs at the point to partition the hard drive. Something is preventing me from partitioning my hard drive. 

Any suggestions? Are there any Windows diagnostics that might disclose the problem? Should I attempt to partition the drive using Windows and then install Edgy or Dapper? Can somebody point me in the right direction?

---

### Post by shareMenaPeace on 2007-02-13
You can try booting the LIVE CD and use from System -> Administration -> Gnome Partition Manager.

Try to manual resize the ntfs partition there again apply the settings than restart and resize the free disk space aswell (1gigabyte). apply - restart now format the big free space to ext3 and the 1gb space partition to linux swap.

If this will not work and if you cant boot windows afterwards you can still backup the data with the live cd and burning backup files.

---

### Post by dtholen on 2007-02-13
The point that bothers me is "if it doesn't work". I am concerned about having to reinstall XP. That was not a pleasant experience in my recent past so I want to avoid it like the plague. I hope there are some safer methods to employ first. Thanks for the advice. Let's see what others are recommending.

---

### Post by alphaakenny1 on 2007-02-13
have you ever thought about creating a backup image of your xp partition

---

### Post by bodhi.zazen on 2007-02-13
> **dtholen said:**
> The point that bothers me is "if it doesn't work". I am concerned about having to reinstall XP. That was not a pleasant experience in my recent past so I want to avoid it like the plague. I hope there are some safer methods to employ first. Thanks for the advice. Let's see what others are recommending.

Well :

[list=number][*]First the advice of alphaakenny1 re: backing up your partition is a good one.
[*]Second there should be no reason to re-install Windows. If you need to repair the MBR that can be done without re-installing.[/list]

Second, well the nice thing about Linux is you can do everything with the CLI.

To partition, use cfdisk from the live CD. Open a terminal and follow this advice :

[http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html](http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html)

You need 10-15 Gb as a root partition, and a swap partition.

IMO, Size of swap is RAM X 2, max 1 Gb.

You can also format via the command line, see here :

[http://www.ubuntuforums.org/showthread.php?t=282018](http://www.ubuntuforums.org/showthread.php?t=282018)

Also, one last thing, you can only haev 4 primary partitions. If you need more then 4 partitions you need to make an extended partition which can then haev logical partitions within it :p

---

### Post by scrooge_74 on 2007-02-13
> **dtholen said:**
> Please, I could really use some help here. I have attempted an Edgy install several times and the install program hangs at the point to partition my hard drive. I have an XP machine with an 80GB hard drive with 50% free space. I attempted both the automatic and manual options to format. It is important to preserve the XP operating system and many important programs that I use when setting up a dual boot environment. 

It was suggested that I use another install CD burned at a slower speed. I did without success. It was suggested that I try to install Dapper. I did and the installation program hangs at the point to partition the hard drive. Something is preventing me from partitioning my hard drive. 

Any suggestions? Are there any Windows diagnostics that might disclose the problem? Should I attempt to partition the drive using Windows and then install Edgy or Dapper? Can somebody point me in the right direction?

FIRST: defrag the HD,  XP will throw files all over the place.  Check while this is been done so you have an idea how much file is space XP will tell are files it cant move.

That will tell you how big is the new partition you will create with UBUNTU.  You are probably trying to make a 50%-50% partitions but probably XP has some files in the 63% space so UBUNTU will hang.  

When you have defrag the disk try making a 35% or 45% new partition and see if it will let you do it.

Hang in there

---

### Post by louieb on 2007-02-13
> **dtholen said:**
>  I am concerned about having to reinstall XP...
Ah but you get a nice clean uncluttered system after a fresh install.
 As one who has trashed an XP install while doing a Linux installation. I now do 1 of 2 things, either backup everything or i get a second drive for my Linux install.  
But if that is not an option then defragment  the the drive before you try to shrink the XP partition. I've seen so post that suggest to defrag a couple of times.

How much memory does the PC have? May want to use the alternate CD if it under 256MB. Experience is what you get after you need it.

---

### Post by dtholen on 2007-02-13
> **louieb said:**
> Ah but you get a nice clean uncluttered system after a fresh install.
 As one who has trashed an XP install while doing a Linux installation. I now do 1 of 2 things, either backup everything or i get a second drive for my Linux install.  
But if that is not an option then defragment  the the drive before you try to shrink the XP partition. I've seen so post that suggest to defrag a couple of times.

How much memory does the PC have? May want to use the alternate CD if it under 256MB. Experience is what you get after you need it.

Louieb, 

I defragged several times, probably four, thinking that each time it would improve. The machine has 512MB memory so that should not be a limitation. I like your definition of experience. 

Here's mine. Wisdom comes from experience and most of that from bad experiences. :)

---

### Post by dtholen on 2007-02-13
> **alphaakenny1 said:**
> have you ever thought about creating a backup image of your xp partition

Hey, that sounds interesting. How do I do that?

---

### Post by dtholen on 2007-02-13
> **bodhi.zazen said:**
> Well :

[list=number][*]First the advice of alphaakenny1 re: backing up your partition is a good one.
[*]Second there should be no reason to re-install Windows. If you need to repair the MBR that can be done without re-installing.[/list]

Second, well the nice thing about Linux is you can do everything with the CLI.

To partition, use cfdisk from the live CD. Open a terminal and follow this advice :

[http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html](http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html)

You need 10-15 Gb as a root partition, and a swap partition.

IMO, Size of swap is RAM X 2, max 1 Gb.

You can also format via the command line, see here :

[http://www.ubuntuforums.org/showthread.php?t=282018](http://www.ubuntuforums.org/showthread.php?t=282018)

Also, one last thing, you can only haev 4 primary partitions. If you need more then 4 partitions you need to make an extended partition which can then haev logical partitions within it :p



As a completely new user, I have not developed a comfort level using Linux or the command line. I find it a little intimidating at this stage. Partitioning is a little mysterious to me but I would probably be better served by doing it from the Windows side (sigh!) :(  I'm just not there yet but that's the direction I would like to travel.

---

### Post by bodhi.zazen on 2007-02-13
> **dtholen said:**
> As a completely new user, I have not developed a comfort level using Linux or the command line. I find it a little intimidating at this stage. Partitioning is a little mysterious to me but I would probably be better served by doing it from the Windows side (sigh!) :(  I'm just not there yet but that's the direction I would like to travel.

LOL

Sure, aren't we all like that ?

It is not too bad, follow the links I gave you.

You may be in a "catch 22"

Depending on how you partition ubuntu may not recognize the partition. IMO cfdisk is most reliable :p

If you go from the windows side, best to partition a number of FAT and then allow ubuntu to reformat.

---

### Post by dtholen on 2007-02-21
I have tried to partition several times without success. Once during the process I received an error message about bad sectors on the hard disk. I contacted HP for information and was referred to Hitachi, the maker of the hard drive, to obtain diagnostics. Running diagnostics showed no errors or bad sectors on the drive. 

I downloaded the alternate CD version and want to attempt installing again. Is there any tutorials available that you can point me to regarding installations using the alternate CD? Is it more text based and therefore perhaps too demanding to the unskilled?

---

### Post by KiwiPete on 2007-02-21
I'm watching this thread with interest as the issues you are describing (and your confidence / experience level) are very much same as mine.

When I've tried re-partitioning my existing XP drive I too get errors describing sector errors and damage, but there is no other evidence supporting that.

I've also tried re-partitioning using GParted on the Live Ububtu CD - it fails - and the Details described something about being unable to partition a "live Windows partition" - sorry I didn't write down the exact phrase. I'm wondering if that is significant.

Can anyone else help us out here?

---

### Post by dtholen on 2007-02-21
> **KiwiPete said:**
> I'm watching this thread with interest as the issues you are describing (and your confidence / experience level) are very much same as mine.

When I've tried re-partitioning my existing XP drive I too get errors describing sector errors and damage, but there is no other evidence supporting that.

I've also tried re-partitioning using GParted on the Live Ububtu CD - it fails - and the Details described something about being unable to partition a "live Windows partition" - sorry I didn't write down the exact phrase. I'm wondering if that is significant.

Can anyone else help us out here?

Thanks KiwiPete, I'm glad to know that I'm not alone here. I just cannot get past this problem and am dead in the water until I do....

---

### Post by bodhi.zazen on 2007-02-21
Here is a tutorial for the alternate CD :

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

As far as the problems, 

1. defragement your windows partition.

2. Try the gparted cd :

GParted:
	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

The version of gparted on that cd is newer then the Ubuntu desktop cd and also contains test disk which may help.

3. Please post the exact error message otherwise it is quite difficult to guess the nature of the problem.

---

### Post by KiwiPete on 2007-02-21
Thanks bodhi.zazen

I re-ran GParted from Live CD to get the exact error messages...

When I try to partition main drive /dev/hda1 (on which XP boots) it fails after finding numerous sector errors. This seems same probalem that dtholen has had.

So I also tried to partition my other hard drive (currently just used for data) - and that fails because "Parted can't resize partitions managed by Windows Dynamic Disk".
I am printing below the full Parted Details file in case that has more info you need. I am not sure about what some of it means.

Any suggestions on getting around this problem?

KiwiPete
-----------------------
GParted 0.2.5

Resize /dev/sda1 from 279.46 GiB to 198.97 GiB    ( ERROR )
     	
check filesystem on /dev/sda1 for errors and (if possible) fix them    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Using locale 'en_US.UTF-8'.
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 300066402816 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 99780 MB (33.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 3233 MB 0
Multi-Record : 93322 MB 9091
$MFTMirr : 66189 MB 1
Compressed : 87645 MB 9666
Ordinary : 135467 MB 10875
You might resize at 99779690496 bytes or 99780 MB (freeing 200287 MB).
Please make a test run using both the -n and -s options before real resizing!
resize the filesystem    ( SUCCES )
     	
run simulation    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1 -s 213639135232 --no-action
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 300066402816 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
New volume size : 213639131648 bytes (213640 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 99780 MB (33.3%)
Collecting resizing constraints ...
Needed relocations : 0 (0 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
The read-only test run ended successfully.
resize the filesystem    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1 -s 213639135232
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 300066402816 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
New volume size : 213639131648 bytes (213640 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 99780 MB (33.3%)
Collecting resizing constraints ...
Needed relocations : 0 (0 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
Successfully resized NTFS on device '/dev/sda1'.
You can go on to shrink the device for example with Linux fdisk.
IMPORTANT: When recreating the partition, make sure that you
1) create it at the same disk sector (use sector as the unit!)
2) create it with the same partition type (usually 7, HPFS/NTFS)
3) do not make it smaller than the new NTFS filesystem size
4) set the bootable flag for the partition if it existed before
Otherwise you won't be able to access NTFS or can't boot from the disk!
If you make a mistake and don't have a partition table backup then you
can recover the partition table by TestDisk or Parted's rescue mode.
resize partition    ( ERROR )
     	
old start: 63
old end: 586067264
old size: 279.46 GiB
Parted can't resize partitions managed by Windows Dynamic Disk.
check filesystem on /dev/sda1 for errors and (if possible) fix them    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Using locale 'en_US.UTF-8'.
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 213639131648 bytes (213640 MB)
Current device size: 300066407424 bytes (300067 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 99778 MB (46.7%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 3233 MB 0
Multi-Record : 93322 MB 9091
$MFTMirr : 66189 MB 1
Compressed : 87645 MB 9666
Ordinary : 135467 MB 10875
You might resize at 99777052672 bytes or 99778 MB (freeing 113862 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition    ( SUCCES )
     	
run simulation    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1 --no-action
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 213639131648 bytes (213640 MB)
Current device size: 300066407424 bytes (300067 MB)
New volume size : 300066402816 bytes (300067 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 99778 MB (46.7%)
Collecting resizing constraints ...
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
The read-only test run ended successfully.
grow filesystem to fill the partition    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 213639131648 bytes (213640 MB)
Current device size: 300066407424 bytes (300067 MB)
New volume size : 300066402816 bytes (300067 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 99778 MB (46.7%)
Collecting resizing constraints ...
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
Successfully resized NTFS on device '/dev/sda1'.
check filesystem on /dev/sda1 for errors and (if possible) fix them    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Using locale 'en_US.UTF-8'.
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 300066402816 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 99780 MB (33.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 3233 MB 0
Multi-Record : 93322 MB 9091
$MFTMirr : 66189 MB 1
Compressed : 87645 MB 9666
Ordinary : 135467 MB 10875
You might resize at 99779690496 bytes or 99780 MB (freeing 200287 MB).
Please make a test run using both the -n and -s options before real resizing!

---

### Post by dtholen on 2007-02-21
KiwiPete, 

You are way out in front of me. I just downloaded and burned the Qparted Live CD. I think I'll wait and see where this leads you. I am overwhelmed with the details you managed to provide. I can't figure out how to copy data when I am booted from a live CD. I'll keep watching as this develops. Glad to have you involved here.

---

### Post by KiwiPete on 2007-02-21
Hi Dtholen

Hang in there - hopefully someone will point us in the right direction...

The only way I managed to copy the Parted Details when booted into Ubuntu from the Live CD was to select the 'Save Details' option and save them to a floppy disk in Ubuntu.

Then when I re-booted to Windows (and got on this forum again) I cut and pasted the details from the floppy disk Deatils.htm file into my post.

KiwiPete

---

### Post by bodhi.zazen on 2007-02-21
KiwiPete :

Well that certainly was a prolific post :p

Yes, I see one set of errors, but I see several successes as well. ;)

Look at this :

Current volume size: 300066402816 bytes (300067 MB)
Current volume size: 300066402816 bytes (300067 MB)
Current volume size: 300066402816 bytes (300067 MB)
[b]Current volume size: 213639131648 bytes (213640 MB)
Current volume size: 213639131648 bytes (213640 MB)
Current volume size: 213639131648 bytes (213640 MB)[/b]
Current volume size: 300066402816 bytes (300067 MB)

This is just a listing of the partition size, and is appears to change.

Can you post information regarding you partition size as you make those changes ...

Also gparted can be run as a gui, not just from the command line ...
that should give you quick information on partition size ...

Last, you have the gparted CD, what happens when you run test disk ??

---

### Post by KiwiPete on 2007-02-21
Hi Bodhi.zazen

Hmmm... I don't know why the volume size changes like that!
All I did was use the (gui) GParted on 6.10 Live CD, select the drive and choose resize.

If you can give me more specific instructions I'll find out more.

I have not got the GParted CD (yet).
I am still using the version on 6.10 Live CD.

I'll be out for the next few hours now (this is New Zealand time so its day over here!)
but will download GParted Cd as you suggest and run test disk and get back to you.

If you have other ideas I can try please give specific instructions - simple language too please for us newbies.

Thanks

KiwiPete

---

### Post by dtholen on 2007-02-21
> **KiwiPete said:**
> Hi Dtholen

Hang in there - hopefully someone will point us in the right direction...

The only way I managed to copy the Parted Details when booted into Ubuntu from the Live CD was to select the 'Save Details' option and save them to a floppy disk in Ubuntu.

Then when I re-booted to Windows (and got on this forum again) I cut and pasted the details from the floppy disk Deatils.htm file into my post.

KiwiPete

Gasp!, I don't have a floppy drive anymore. But I bet I could use a USB Flash Drive and get the same results. I will be trying to use the new Qparted version, hopefully, sometime in the next 24 hours. This stuff really takes a lot of time and there are so many other things to do!

---

### Post by dtholen on 2007-02-21
I downloaded and burned a copy of Qparted Live CD. After running the program the same error message reported previously is received. Selecting the /dev/hda1 partition results in "Error: This software had deteted that the disk has at least 80 bad sectors. Unable to read the contents of this filesystem! Becaues of this some operations may be unavailable."

Because of this message a couple of days ago I obtained diagnostics from the hard disk manufacturer (Hitachi, model no: IC25N080ATMR04-0). Running the diagnostics results in no errors being detected. 

Installation is impossible until I can overcome these partitioning problems.

---

### Post by antoz on 2007-02-21
Using Windows to do any partitioning or formatting would be the last thing I would attempt unless you want to wipe your whole hardrive.
I am not all that experienced with Ubuntu but I have in the past rezised partitions using the live CD without losing any data, I have also split partition and created new ones using an Akronis rescue disk BUT I would never trust Windows to do any of that.
Have fun

---

### Post by dtholen on 2007-02-22
Bump

---

### Post by dtholen on 2007-02-22
I know that Windows scatters files all over the hard disk. I have also been told that if a file is not fragmented it will not be moved when defragging. When I defrag, the disk map still shows what appears to be files scattered in the area of the disk that could be available for partitioning. While you may have 50% of a hard drive available is it possible that the space is not available for partitioning because a few files occupy the space? If so, what can be done to identify and move these files making the area available for re-partitioning? Does this seem logical and perhaps a reason why I cannot partition my hard drive to allow installing Ubuntu.

---

### Post by bodhi.zazen on 2007-02-22
Yes, as we discussed in previous posts, you must defragment your windows partition as a first step.

If you have not done so, defragment and re-try partitioning from the Ubuntu or gparted CD.

---

### Post by dtholen on 2007-02-22
I have defragged within Windows using the Microsoft product, used Diskeeper and Auslogic Disk Defrag. Then tried Qparted Live CD again and the error message persists. Can you recommed any utilities that would do a better job moving files creating  a clean space available for partitioning? How can I determine visually that the space is clear of files and available for partitioning. I currently have one partition on the disk, a Windows NTFS.

---

### Post by ebichuhamster on 2007-02-23
dtholten I thimk I'm expiriencing the same problem as you.  My Ubuntu starts up well from the install disk, everything is going neat and tidy.  I partition the disks as has been suggested in this forum and other ubuntu noob sites.  But then the error without error message occurs:

It says more or less

dev/hda1 could not be resized from 99.9Gb to 40.00Gb. See details for information.

Details:

0 out of 2 tasks completed

Failed to resize from 99.9Gb to 40.00Gb.

Failed to create 58.54Gb extended partition.


I really dont want to just partition my drive, I think i can do this with Partition Magic.  My interest is in finding out why, just as dtholten, why o why cant Ubuntu make the partition.

---

### Post by dtholen on 2007-02-23
The following is the error message I consistently receive when trying to partition. Are there any further clues here?

GParted 0.2.5

Resize /dev/hda1 from 74.52 GiB to 50.08 GiB    ( ERROR )
     	
check filesystem on /dev/hda1 for errors and (if possible) fix them    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/hda1
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Using locale 'en_US.UTF-8'.
Device name : /dev/hda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 80015491584 bytes (80016 MB)
Current device size: 80015491584 bytes (80016 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 41903 MB (52.4%)
Collecting resizing constraints ...
WARNING: The disk has bad sector! This can cause reliability problems!
Bad clusters: 14753909 - 14753909
Bad clusters: 14753978 - 14753978
Bad clusters: 14754047 - 14754047
Bad clusters: 15125736 - 15125740
Bad clusters: 15125802 - 15125810
Bad clusters: 15126008 - 15126016
Bad clusters: 15138408 - 15138416
Bad clusters: 15138482 - 15138490
Bad clusters: 15138548 - 15138556
Bad clusters: 15138614 - 15138622
Bad clusters: 15138680 - 15138688
Bad clusters: 15138746 - 15138754
ERROR: The NTFS volume has at least 80 bad sectors.
****************************************************************************
* WARNING: The disk has bad sector. This means physical damage on the disk *
* surface caused by deterioration, manufacturing faults or other reason. *
* The reliability of the disk may stay stable or degrade fast. We suggest *
* making a full backup urgently by running 'ntfsclone --rescue ...' then *
* run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize *
* NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
****************************************************************************

========================================

---

### Post by KiwiPete on 2007-02-23
For some reason the 6.10 Ubuntu installer seems to throw up these bad sector errors.. I had this problem when trying to partition my main hard drive (previously the sole domain of Win XP).

So I tried using my second hard drive - and got around the bad sectors problem - but discovered a new problem - "unable to resize partitions managed by Windows Dynamic Disk".
Everything I can find about Windows Dynamic Disk seems to suggest this problem is a big one. I thought about buying Partition Magic to do the partitioning myself - but saw a comment somewhere that even Partition Magic cannot do anything with this Dynamic Disk thing.

Frustration reigns:( 

From this thread there seem to be at least three of us facing the same problems.
We cannot be unique.
Can anyone help us:confused: 

KiwiPete

---

### Post by dtholen on 2007-02-23
I have tried Qparted, Gparted but not yet "Dparted" ):P Maybe I'll have to find another more constructive hobby, like brewing beer!;)

---

### Post by ebichuhamster on 2007-02-24
^_^ i finally got it to resize the partition!!

a friend of mine used "ULTIMATE BOOT CD" and discovered "inconsistencies" in the drive, an error which is not displayed on either partition magic or gparted (the ubunto program used for partitioning on instal),,,

Neither i nor he know wtf are inconsistencies in english, so he just ran the autocheck for the Hard drive option on **Properties** option in windows

it took an hour and a half, maybe more, but that did it.  

After that i resized the ntfs partition with PartitionMagic, but i think after you have solved the "inconsistencies" you can partition with Gparted or any other.

Good Luck! Hope i helped!

---

### Post by ebichuhamster on 2007-02-24
while im in here.. i know this is veering off topic but i cant find anywhere specific to talk about this other problem:

Installation went smoothly after partition problem, but now, after having uploaded Ubunto tto see if it was working, i restarted it and it doesnt get to the Window Manager interface.  I get the fading screen thing, (which im not sure, but i think it's normal) then nothing hapes,, the whole screen just goes black and there im stuck.>_<

Anyone wanna point me in the right direction?

---

### Post by dtholen on 2007-02-24
> **ebichuhamster said:**
> while im in here.. i know this is veering off topic but i cant find anywhere specific to talk about this other problem:

Installation went smoothly after partition problem, but now, after having uploaded Ubunto tto see if it was working, i restarted it and it doesnt get to the Window Manager interface.  I get the fading screen thing, (which im not sure, but i think it's normal) then nothing hapes,, the whole screen just goes black and there im stuck.>_<

Anyone wanna point me in the right direction?

Ebichuhamster, 

I would respectfully ask that your repost your question to another thread or create your own. Several of us here have invested a lot of time and effort toward this problem and it seems that there are many who share this situation. Creating your own thread is not difficult and you will obtain more specific answers. 

Thanks

---

### Post by dtholen on 2007-02-25
Bump

---

### Post by KiwiPete on 2007-03-05
Hi dtholen - just wondering if your problems have been resolved?
I'm still struggling to find a way to re-partition - Gparted can't do it as far as I can see.

KiwiPete

---

### Post by dtholen on 2007-03-05
KiwiPete,

I have spent a lot of time trying to resolve this issue. Most recently I have run several diagnostics on my hard drive since the attempted installation seemed to indicate that I have bad sectors. I contacted Hitachi, the manufacture of the drive, and obtained their diagnostics which revealed nothing. HP, the manufacturer of the computer, directed me to diagnostics that reside in the BIOS. There are two versions, a short test and a long test. The short test passed but the long test failed. HP said that I need to replace the hard drive. I ordered a new one and am awaiting its arrival. Now my next adventure will be to learn how to install a new drive in my laptop and clone the old one without loosing any data. I remain optimistic about Ubuntu and getting it installed. I will not give up.

---

### Post by steve.horsley on 2007-03-05
> **dtholen said:**
> The following is the error message I consistently receive when trying to partition. Are there any further clues here?

GParted 0.2.5

Resize /dev/hda1 from 74.52 GiB to 50.08 GiB    ( ERROR )
     	
check filesystem on /dev/hda1 for errors and (if possible) fix them    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/hda1
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Using locale 'en_US.UTF-8'.
Device name : /dev/hda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 80015491584 bytes (80016 MB)
Current device size: 80015491584 bytes (80016 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 41903 MB (52.4%)
Collecting resizing constraints ...
WARNING: The disk has bad sector! This can cause reliability problems!
Bad clusters: 14753909 - 14753909
Bad clusters: 14753978 - 14753978
and lots more...


This could be one of two things: 
1) Linux is having difficulty with your hardware and can't read the hard disk reliably, or (more likely):
2) The NTFS filesystem has errors.

My first step would be to try to run chkdsk in Windows to see if that clears the errors. Unfortunately, I can't tell you how to do this because I don't know.

I would also suggest trying Partition Magic to shrink the Windows partition. Partly because it may feel more familiar and safer to you, and partly so you can't blame Linux if it screws up. MAKE A BACKUP FIRST.

Once you have resized the Windows partition, you can use the Ubuntu installer option to use the remaining free space on the disk, and the installer will then make its own partitions to put Ubuntu on. This is an easy and stres-free way to install. Just make sure you don't click to erase and use the whole disk by mistake.

---

### Post by dtholen on 2007-03-09
Success has finally arrived at my doorstep! I purchased a new hard drive for my laptop, a Seagate 120GB, cloned the old drive to the new, installed the new drive and successfully installed 6.10 without incident. Apparently the hard drive did have problems that prevented partitioning.  Now I am successfully dual booting with Windows XP. Looking forward now to the learning experience. Thanks for everyone's help and advice. On with the show!:-P

---

### Post by bodhi.zazen on 2007-03-10
Welcome to Ubuntu :)

Glad it all worked out ...

---

