---
title: "Ubuntu partitioner problem"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by Terrycymru on 2005-10-26
I want to install Ubuntu to dual boot with the existing WinME on my computer. it has a 20gb disk with little on it except the operating system and a few apps such as Opera so there must be about 18gb of unused space! I assume it is all on one partition. I have never used partitions before so I am on a steep learning curve. Please bear with me.

Ubuntu install CD runs into a problem when it gets to the partitioner. It will not let me change the size of the partition. The first run using the automatic method said it was not possible to resize the partition. I cannot remember the precise message or precisely what I did before re-booting.

I have read several very helpful web pages on the subject but even when I  use the manual method the resize does not take place. This is what I see when I select Manually in Partition Disks:

IDE master (hda) - 20.5 GB Maxtor 2B020H1
#1 primary            20.5 GB [arrow] [smiley] fat 32 /media/hda1

Of course, [arrow] and [smiley] are graphics.

What does this all mean - have I inadvertently changed the partition in some way? What should I try next?

---

### Post by wishyjr on 2005-10-26
hiya, 
firstly, i'd recommend manually editing your hard drive partitions if your dual booting. I think that the auto-process fails because you need a ext3 formatted partition but because windows is on that partition it'll try and stay away using that partition hence it wont resize it.

Cant remember exactly what the commands are in the partitioner but if you edit the drive manually you should find something that says 'resize partition' somewhere.

so cut a chunk out for ubuntu to go on and mount it as '/'. You'll see what i mean when you actually do it. :)

then make another small one thats about double the size of your systems RAM. Use this as a 'swap file'

see how far you get, any problems post back!

and remember, changes wont take effect until you've done all the changes and tell ubuntu to write the changes to disk! 

good luck

---

### Post by Terrycymru on 2005-10-26
[QUOTE=wishyjr]hiya, 
firstly, i'd recommend manually editing your hard drive partitions if your dual booting. I think that the auto-process fails because you need a ext3 formatted partition but because windows is on that partition it'll try and stay away using that partition hence it wont resize it.
[/QUOTE]

But I've only got 1 partition and that has WinMe on it! Are you saying that Ubuntu's partitioner cannot cope with this situation? What is the alternative?

[QUOTE=wishyjr]
Cant remember exactly what the commands are in the partitioner but if you edit the drive manually you should find something that says 'resize partition' somewhere.
[/QUOTE]

Yes, I have tried to resize manually but it very quickly goes back to the Partition Disks screen with no changes.

---

### Post by wishyjr on 2005-10-26
what i meant was ubuntu wont automatically resize the partition because it knows winME is on it. You should, in therory, have to do it manually. The partitioner can handle such a situation, in fact i've found it to be one of the best partitioners ive used!

can you post up all of the options you select to resize the partition?

btw: there are loads and loads of threads on partitioning issues, you should try the search function on these here forums!

---

### Post by Terrycymru on 2005-10-26
[QUOTE=wishyjr]can you post up all of the options you select to resize the partition?[/QUOTE]

I'll go and do it now. I'll be back later.

---

### Post by Terrycymru on 2005-10-26
[QUOTE=wishyjr]what i meant was ubuntu wont automatically resize the partition because it knows winME is on it. You should, in therory, have to do it manually. The partitioner can handle such a situation, in fact i've found it to be one of the best partitioners ive used!

can you post up all of the options you select to resize the partition?

btw: there are loads and loads of threads on partitioning issues, you should try the search function on these here forums![/QUOTE]

I've searched the forums on partitioning issues. Nothing there that covers my problem. Anyway, here are details of the options I selected:

Partition Disks 

Partition method: Manually edit partitions table

--------------
IDE master (hda) - 20.5 GB Maxtor 2B020H1
#1 primary 20.5 GB [arrow] [smiley] fat 32 /media/hda1

HIGHLIGHT #1 primary 20.5 GB [arrow] [smiley] fat 32 /media/hda1
<Enter>
-------------
Partition settings :

Use as :               FAT32 file system
Mount point:         /media/hda1
Mount options:      defaults
Bootable flag:       on
Size:                   20.5 GB

HIGHLIGHT Size:    20.5 GB
<Enter>
-------------
Before the resize operation takes place, the change has to be written to diskYou cannot undo this operation...
Write the changes to disk and resize the partition? <Yes>
------------
New partition size: 20.5 GB
Change to 8.0 GB <continue>
------------

After a few seconds goes back to Manually Partition Disks screen with unchanged details:
 
IDE master (hda) - 20.5 GB Maxtor 2B020H1
#1 primary 20.5 GB [arrow] [smiley] fat 32 /media/hda1

As I undestand it I should at this stage see details of resized #1 partition and free space created. This does not happen.

---

### Post by Terrycymru on 2005-10-26
Can anyone help?

All the necessary details of the problem are above.

---

### Post by paddyg on 2005-10-26
Have you tried resizing your windows partition by using win programs like Partition Magic?

Or....
Why don't you dualboot Win XP and ubuntu (Windows installed first [it should do all the job---partition the disk and all], ubuntu next)?

---

### Post by wishyjr on 2005-10-26
so what are your intentions here? you want the winME partition to be 8GB? or do you want to 'cut out' 8GB for ubnutu? You have this:

[B]HIGHLIGHT Size: 20.5 GB
<Enter>
-------------
Before the resize operation takes place, the change has to be written to diskYou cannot undo this operation...
Write the changes to disk and resize the partition? <Yes>
------------
New partition size: 20.5 GB
Change to 8.0 GB <continue>
------------[/B]

i dont quite understand the last part though, how can the 'new partiton size' be the same as the old one? 20.5 - 8 = 12.5 yes? If i remember correctly dont you have to specify your origional (i.e. winME) partition's new size?

---

### Post by Terrycymru on 2005-10-26
[QUOTE=wishyjr]so what are your intentions here? you want the winME partition to be 8GB? or do you want to 'cut out' 8GB for ubnutu? You have this:

[B]HIGHLIGHT Size: 20.5 GB
<Enter>
-------------
Before the resize operation takes place, the change has to be written to diskYou cannot undo this operation...
Write the changes to disk and resize the partition? <Yes>
------------
New partition size: 20.5 GB
Change to 8.0 GB <continue>
------------[/B]

i dont quite understand the last part though, how can the 'new partiton size' be the same as the old one? 20.5 - 8 = 12.5 yes? If i remember correctly dont you have to specify your origional (i.e. winME) partition's new size?[/QUOTE]

[B]I want WinME partition to be 8GB leaving 12.5 for Ubuntu.

New partition size comes up by default as all of disk. I changed to 8GB but, as described above, it did not work.[/B]

---

### Post by tonysathre on 2005-10-26
check the checksum of the ISO image, or redownload and reburn the CD at a slow speed

---

### Post by erikpiper on 2005-10-26
Yes, these cd's are very sensitive. I normally burn at only 6X speed. No problems that way. A disk I burned at 42X didn't even boot totally.

---

### Post by Terrycymru on 2005-10-27
[QUOTE=tonysathre]check the checksum of the ISO image, or redownload and reburn the CD at a slow speed[/QUOTE]

Thanks for your reply. I've used Fastsum to check the checksum of the iso file. It is 126751A2DC5528C2F9044D9E4EE36D61 which is correct. I burned the CD at 4X.

I may be wrong but I don't think there is anything wrong with the CD.
Has **anyone**  got the partitioner to work with WinME on the only partition?

---

### Post by john_c on 2005-10-27
I haven't resized a partition on Win me but did a Win98 partition very recently using Qtparted.  It also was a FAT filesystem.

If all else fails you could try that.  It is included on the System Rescue cd (download the .iso from [http://www.sysresccd.org/)](http://www.sysresccd.org/)).  It is a live cd so very easy to use.  The Simply Mepis live/install cd's also have Qtparted.

Make sure you defrag the disk with the Windows software (or whatever else is available) first - also may wish to make a back up just in case.

Good luck,

John_c

---

