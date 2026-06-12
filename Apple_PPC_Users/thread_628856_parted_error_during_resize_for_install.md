---
title: "parted error during resize for install"
date: 2007-12-01
forum: Apple PPC Users
---

### Post by anthonylane13 on 2007-12-01
I am trying to get my first ubuntu install going, but having some issues regarding resizing my HFS+ partition (Mac HD) in order to have a space for ubuntu.

I have followed this advice so far:
disable journaling on mac hd
run ubuntu installer until partitioner
go to shell
type: parted
type: print
(shows list of partitions)
I then type:
resize 5 360 450000
my partition size is currently 60GB, and I want to use 15GB for ubuntu.  I have only 22GB of data on this disk.

parted gives me this error:
Unable to satisfy all constraints on the partition.

Can anyone enlighten me as to what that means, and what I can do to solve the problem and get ubuntu on my mac (powerbook g4)

Thank you

---

### Post by Auria on 2007-12-01
Perhaps try the partition editor with a GUI found in the menus of the LiveCD [if you are using the LiveCD, that it]

---

### Post by jmelton on 2007-12-01
> **anthonylane13 said:**
> I am trying to get my first ubuntu install going, but having some issues regarding resizing my HFS+ partition (Mac HD) in order to have a space for ubuntu.

I have followed this advice so far:
disable journaling on mac hd
run ubuntu installer until partitioner
go to shell
type: parted
type: print
(shows list of partitions)
I then type:
resize 5 360 450000
my partition size is currently 60GB, and I want to use 15GB for ubuntu.  I have only 22GB of data on this disk.

parted gives me this error:
Unable to satisfy all constraints on the partition.

Can anyone enlighten me as to what that means, and what I can do to solve the problem and get ubuntu on my mac (powerbook g4)

Thank you

What was the output of the print command?  

On my iBook the OS X partition is partition 3, and according to print the starting and ending blocks are at 134MB and 40GB, so if I wanted to resize my hfsplus partition down by 10GB, I would enter:
resize 3 134MB 30GB

I don't know if that helps; hope so.

I did my resizing from the Live CD before actually entering the install process, although I think you can do it either way.  And, of course, I backed up the important data from my OS X partition before I resized it, just in case anything went wrong, but thankfully that and the install went perfectly (aside from wireless not working) and I was booting into Ubuntu within 45 minutes.

---

### Post by anthonylane13 on 2007-12-02
> **jmelton said:**
> What was the output of the print command?  

On my iBook the OS X partition is partition 3, and according to print the starting and ending blocks are at 134MB and 40GB, so if I wanted to resize my hfsplus partition down by 10GB, I would enter:
resize 3 134MB 30GB

I don't know if that helps; hope so.

I did my resizing from the Live CD before actually entering the install process, although I think you can do it either way.  And, of course, I backed up the important data from my OS X partition before I resized it, just in case anything went wrong, but thankfully that and the install went perfectly (aside from wireless not working) and I was booting into Ubuntu within 45 minutes.

The output of the print command showed 5 partitions listed; I thought this to be strange as I have not partitioned it at any other time. Disk utility on Mac OS X only shows a single partition.

Unfortunately, I couldn't get the live CD to work (7.04) so I'm using the dapper alternate CD.  Any thoughts?

Thanks for all replies so far :-)

---

### Post by jmelton on 2007-12-02
> **anthonylane13 said:**
> The output of the print command showed 5 partitions listed; I thought this to be strange as I have not partitioned it at any other time. Disk utility on Mac OS X only shows a single partition.

Unfortunately, I couldn't get the live CD to work (7.04) so I'm using the dapper alternate CD.  Any thoughts?


I don't think that the disk utility in OS X shows boot partitions and such.  But the print command shows your OS X partition as partition 5?  That's strange!  What are the other partitions it lists?

On mine I have 5 partitions now but had 3 before.  When I started installation, print listed the starting and ending points of the OS X partition as 134 MB and 60GB, so to resize it I typed in 134MB and 40GB as the start and end points.  I take it from your resize command that print shows the start and end points of your partition as block numbers rather than megabyte or gigabyte locations?  Not that that would matter as long as you're entering the correct numbers.  Here's what I get when I print the partitions on my machine (leaving out the size listing):


number      start        end           type          name
1               0.51kb     32.8kb                       Apple
3               134MB     40MB         hfs+         Customer
2               40GB       40GB         hfs           untitled-- boot
4               40GB       59.1GB      ext3          (This is, of course, the Ubuntu / partition)
5               59.1GB    60.0GB      swap

I'm baffled what those other two partitions are on your machine.  :confused:

Oh, why are you installing Dapper instead of Feisty or Gutsy?  Were there not alternate install disks available for those?

---

### Post by anthonylane13 on 2007-12-02
> **jmelton said:**
> 

I'm baffled what those other two partitions are on your machine.  :confused:

Oh, why are you installing Dapper instead of Feisty or Gutsy?  Were there not alternate install disks available for those?

Thanks for your reply - I'm baffled too...

Here's what parted delivers on the print command:

Number     Start     End     Size     File System     Name
1                1kb        32kb    32kb                           Apple
2               33kb       65kb    33kb                           Macintosh
1               66kb       98kb    33kb                           Macintosh
1               98kb      360kb   262kb                         Patch Partition
1              360kb      60GB    60GB     hfs+             MacOS

I'm installing dapper because the fiesty live cd I bought didn't work, and the man at the shop recommended the dapper as being stable and not likely to give me any problems.

Any thoughts?

---

### Post by jmelton on 2007-12-02
> **anthonylane13 said:**
> Thanks for your reply - I'm baffled too...

Here's what parted delivers on the print command:

Number     Start     End     Size     File System     Name
1                1kb        32kb    32kb                           Apple
2               33kb       65kb    33kb                           Macintosh
1               66kb       98kb    33kb                           Macintosh
1               98kb      360kb   262kb                         Patch Partition
1              360kb      60GB    60GB     hfs+             MacOS

I'm installing dapper because the fiesty live cd I bought didn't work, and the man at the shop recommended the dapper as being stable and not likely to give me any problems.

Any thoughts?

Wouldn't the partition number for MacOS be 5, not 1?  If so, then I think the format of the resize command you want to resize your Mac partition to 45 gigs would be something like:

resize 5 360kb 45GB

If the print command really is showing four different partitions numbered 1, then I guess that would be a problem when you're trying to issue a resize command since the format includes a partition number.

---

### Post by anthonylane13 on 2007-12-02
Sorry!!! That was a typo - the partition numbers were 1-5 as you would expect.  I typed in 
resize 5 360 450000
and got the error message
Unable to satisfy all constraints on the partition.

The only thing that's occurring to me is that my disk journaling is not registering.  I used the terminal in OSX
sudo diskutil enableJournal Macintosh\HD/

and then

sudo diskutil disableJournal Macintosh\HD/

I'm expecting a message to say that journaling is disabled, but I get this:
Disk Utility Tool       ?2002-2003, Apple Computer, Inc.
Usage:  diskutil [enableJournal|disableJournal] [Mount Point|Disk Identifier|Device Node]
Enable or disable journaling on a mounted HFS Extended volume.
Ownership of the affected disk is required.
Example: diskutil enableJournal /

But if I use the disk utillity GUI it says that the disk is not journaled. Maybe my mac is buggy in this area? Any help greatly appreciated... Thanks for all help so far :-)

---

### Post by jmelton on 2007-12-02
The parted user's manual section on resize says:

>Command: resize minor start end

    Resizes the partition with number minor. The partition will start start from the beginning of the disk, and end end from the beginning of the disk. resize never changes the minor number. Extended partitions can be resized, so long as the new extended partition completely contains all logical partitions.

    Note that Parted does not require a file system to be "defragged" (Parted can safely move data around if necessary). It's a waste of time defragging. Don't bother!

    Supported file systems:

        * ext2, ext3 - restriction: the new start must be the same as the old start.
        * fat16, fat32
        * linux-swap
        * reiserfs (if libreiserfs is installed) 

    Example:

    (parted) resize 3 200 850

    Resize partition 3, so that it begins 200 megabytes and ends 850 megabytes from the beginning of the disk. 
>


So probably if you just say 360 without specifying anything it reads it as 360 megabytes, but the beginning of your partition is 360kb, not 360MB.  Also, if I'm counting the zeros correctly, if it defaults to reading 450000 as 450000 megabytes, that would be 450 gigabytes rather than the 45 gigabytes that you want.

I'm not sure what you would want to call the OS X volume when issuing the diskutil disablejournal command, but I assume the naming conventions are similar to those used in Linux.  So, it's possible that there's something else you should call it instead of Macintosh\HD.  I'm just guessing that might be what's wrong; you can find out for sure what you should call it if you type mount when you're in a terminal and see what it lists as the mount point, disk identifier, and/or device node for the OS X partition.  It sounds like your journaling may already be disabled, though.

---

### Post by anthonylane13 on 2007-12-03
A partial success - indeed, by finding out what my computer likes to refer to my HDD as (NOT Macintosh HD), I was able to disable journaling via the shell, and run parted during my ubuntu install.

However, after about 20 seconds of very encouraging noises, I got the following errors:
Error: Trying to register an extent starting block at 0xAF0429, but another one already exists at this position. You should check the file system!
Error: Could not cache the file system in memory.
Error: Data relocation has failed.
Error: Resizing the HFS+ volume has failed.

I don't really know what this means though...

---

### Post by anthonylane13 on 2007-12-06
Anyone got any suggestions?

I suppose it's telling me that the command to shrink the partition is conflicting with the partition data as it currently stands?

The partition to shrink is no 5:

Number Start End Size File System Name
1 1kb 32kb 32kb Apple
2 33kb 65kb 33kb Macintosh
3 66kb 98kb 33kb Macintosh
4 98kb 360kb 262kb Patch Partition
5 360kb 60GB 60GB hfs+ MacOS

and the command I entered in parted was:
resize 5 360kb 45MB

Then I got this error:
Error: Trying to register an extent starting block at 0xAF0429, but another one already exists at this position. You should check the file system!
Error: Could not cache the file system in memory.
Error: Data relocation has failed.
Error: Resizing the HFS+ volume has failed.

Thanks in advance for any help offered

---

### Post by anthonylane13 on 2007-12-11
I'd be very happy if anyone out there can help... ](*,)

---

