---
title: "Specify Ubuntu install partition multidrive multiboot"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by msfisher on 2007-03-21
I'm new to Ubuntu but only somewhat new to Linux.  I've seen problems similar to mine threaded elsewhere on the forum, but no one set up quite like me.  I have a two-drive system, Windows 98SE on the primary drive which is split into three partitions (hda1, hda2, hda3).  The second drive is split into five partitions, a FAT32 hdb1, Xandros on hdb2 (please don't flame me, I'm moving away from Windows and Xandros makes for a more Windows-like UI and access to games) and, right now, Mandriva 2007 on hdb3.  There's also an ext2 hdb5 (no hdb4) and swap at hdb6.  hdb2 and 3 are both formatted ReiserFS.  I'd like to replace Mandriva with Ubuntu 6.1 or at least load it onto hdb5.  The installers for Mandriva and Xandros gave me that option, but Ubuntu doesn't want to install either place, even when I use the install where I control the load location. I haven't used the Ubuntu formatter to format either partition. I didn't write the exact error down, but I think it didn't want to use either partition as root.

So my question, probably poorly explained and asked, is simply whether there is a way to get Ubuntu loaded to one of these two partitions without messing up hdb3.  

Many thanks in advance.

For the curious, I'm dumping Mandriva because I can't get its network setup to run at a reasonable speed, internet or Mandriva updates, and when I've asked about it, I got  more attitude than help.

---

### Post by bodhi.zazen on 2007-03-21
Depends on the error message.

You may be experiencing this bug , I'm not sure ...

[http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29)

hard to know without the error message ???

---

### Post by msfisher on 2007-03-22
Bodhi.zazen:  Thanks for the reply.  Topic of the link looks close, but I'm not sure.

Let's not worry about errors or error messages and assume I'm thoroughly dumb:

How to I get Ubuntu to install root to a specific, pre-formatted partition when there are other installations present?  Is it as simple as using the advanced partition manager and specifying that the installation partition be formatted?  Since I'm multibooting at least one other Linux distro and Win98, should I specify some other mount point?

For example, when I installed Mandriva (with Win98 and Xandros already installed), I had to use its equivalent to the Ubuntu partition manager to tell it I wanted root on a specific partition without altering the partition.  Although it complained, it went ahead and installed to that partition and boots just fine.  That's what I'm looking for.  

Many thanks!

---

### Post by bodhi.zazen on 2007-03-22
Hard to know where you are getting stuck.

How about a picutre ?

[https://help.ubuntu.com/community/GraphicalInstall#head-49944d8626113375eea234aa41d06d657ae5d6bf](https://help.ubuntu.com/community/GraphicalInstall#head-49944d8626113375eea234aa41d06d657ae5d6bf)

As you can see, at this step you are asked what partition to install into.

You partitions should show up. If they do not select the "Manually Edit the Partition Table" radio box.

The rest of the page will walk you through an install.

If that does not fix your problem, well you did mention an error message. I am not sure if I can help much without knowing the error message. Even then, I may not know.

---

### Post by JoxBG on 2007-03-22
I'm with Bodhi, select manual partition of disk. It should show all existing partitions, including where Mandriva is installed. If you choose that partition, the next menu, top entry should show a do not format default entry. Toggle that and it will change to format partition. If I remember correctly, the next netry is mount point. If you select that it should offer you a menu, select / or root partition. I believe that's all you need. Then scroll to the lower part of the entries (this can get hidden in small windows) and choose Done with this partition or something like. Follow the installer for next steps.

PS. I'm recalling the steps from my server install (always like a fast system), but I'm sure the more exoteric GUI version has equivalent functionality.

---

### Post by msfisher on 2007-03-24
Bohdi.zazen, thanks again; JoxBG thanks, too.  The walkthru came up short, though.  

I went through the install again and stopped, actually just short of where I think I saw some sort of error ( I DON’T remember what error, just accept that at one particular point, the install failed).  Please, get me past this point and I think it will be OK.

At the installation screen "Select a Disk" I see a choice of two drives /dev/hda and /dev/hdb plus the choice to manually edit.  I chose hdb.

I get the choices of completely erasing, resizing hdb5 (which only allows me to use 18 of 20 gigs) or manually edit.  I chose (per JoxBG and the desire not to use the whole drive and the fact there is no unformatted free space) manual edit.

The partitioner starts and I get the Prepare Partitions screen.  I display my hdb and get the following

/hdb1   fat32
/hdb2   reiserFS
/hdb3   reiserFS
/hdb4   extended
   /hdb5   ext2
   /hdb6   linux swap

All as I expected.  I click on/highlight the graphic and/or tabular listing for hdb3, then select Forward.

Up comes the problem screen:  Prepare Mount Points

"Select which partitions you want to use for your new installation and where you want to mount each of them.  You must mount one partition on the root file system ("/") and you must choose at least one partition for use as swap space."  

I've partly abbreviated the table, but it's close to

Mount Point                              Partition                          Format?
(drop down list box)                 (rollover list)
/media/hda6               19GB     ...ATA1  logical   hda6       No
/media/hdb5               20GB     ...ATA2  logical   hdb5       No
/media/hda1               28GB     ...ATA1  primary  hda1       No
/media/hdb1               12GB     ...ATA2  primary  hdb1       No
/media/hdb3               20GB     ...ATA2  logical    hdb3       No
/media/hdb2               20GB     ...ATA2  primary  hdb2       No
/media/swap                 2GB     ...ATA2   logical   hdb6       Yes

I tried eliminating all of the /media entries except the two of interest to my install – hdb3 and swap, format hdb3, but it didn’t work.  I guess this is the spot that I need help getting past.  In order to mount root at hdb3, what do I do?  Is it as simple as changing /dev/hdb3 to root (“/”) and saying yes to format (since hdb3 is ReiserFS and the Ubuntu default is ext3)?  Does anything else need to be changed?

---

### Post by bodhi.zazen on 2007-03-24
> **msfisher said:**
> I tried eliminating all of the /media entries except the two of interest to my install – hdb3 and swap, format hdb3, but it didn’t work.  I guess this is the spot that I need help getting past.  In order to mount root at hdb3, what do I do?  Is it as simple as changing /dev/hdb3 to root (“/”) and saying yes to format (since hdb3 is ReiserFS and the Ubuntu default is ext3)?  Does anything else need to be changed?

1. Yes, If you want to install to hdb3, change the mount point from /media/hdb3 to /

IMO it is a good idea to reformat hdb3 ( / ).

Re-formatting swap is optional.

2. The other mount points are for the remaining partitions. If you want say /dev/hdb1 to mount as /media/hdb1, leave it as is.

If you want /dev/hdb1 to mount at /home /boot /var /media/music , etc change form /media/hdb1 to /home or what have you.

If you do not want to mount /dev/hdb1 change mount point to "none".

You can easily change later by editing /etc/fstab.

---

### Post by msfisher on 2007-03-24
THANKS.  Just what I was looking for.  Maybe the Ubutnu developers could make this a bit clearer for those of us less familiar with the terminology.

---

### Post by msfisher on 2007-03-24
OK, Bohdi I tried it.  Now I know what the error was -- "No root file system!"

The prepare mount points table looks like this

Mount Point      Size      Partition                       Reformat?
/media/hda6     19GB     ...ATA1  logical   hda6     No
/media/hdb5     20GB     ...ATA2  logical   hdb5     No
/media/hda1     28GB     ...ATA1  primary  hda1     No
/media/hdb1     12GB     ...ATA2  primary  hdb1     No
/                     20GB     ...ATA2  logical    hdb3     Yes
/media/hdb2     20GB     ...ATA2  primary  hdb2     No
/media/swap      2GB     ...ATA2   logical    hdb6     No

Pressing forward gives me the no root file system error.  I tried using hdb5, same result.  I tried NOT reformatting, same result.

What am I doing wrong?

Is it possible that this is easier in either 6.06 or the 7.04 beta?  Even Ubuntu-based Linux Mint?  Sorry, I'm getting real frustrated.  I simply didn't have this kind of trouble with either of the other two Linux distros I currently have.

---

### Post by bodhi.zazen on 2007-03-24
> **msfisher said:**
> OK, Bohdi I tried it.  Now I know what the error was -- "No root file system!"

The prepare mount points table looks like this

Mount Point      Size      Partition                       Reformat?
/media/hda6     19GB     ...ATA1  logical   hda6     No
/media/hdb5     20GB     ...ATA2  logical   hdb5     No
/media/hda1     28GB     ...ATA1  primary  hda1     No
/media/hdb1     12GB     ...ATA2  primary  hdb1     No
/                     20GB     ...ATA2  logical    hdb3     Yes
/media/hdb2     20GB     ...ATA2  primary  hdb2     No
/media/swap      2GB     ...ATA2   logical    hdb6     No

Pressing forward gives me the no root file system error.  I tried using hdb5, same result.  I tried NOT reformatting, same result.

What am I doing wrong?

Is it possible that this is easier in either 6.06 or the 7.04 beta?  Even Ubuntu-based Linux Mint?  Sorry, I'm getting real frustrated.  I simply didn't have this kind of trouble with either of the other two Linux distros I currently have.

lol You are doing nothing wrong, what you have now is a bug. It has been described and reported ;)

Here is 1 potential work around :

[http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29)

Edit : This is an uncommon problem, I would suspect it is a problem with ubiquity (ubiquity = installer program) and since you have this problem you may have it with any Ubuntu based distro.

If you wanted to try something new, try the alternate CD :

Here is a how to :  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by StGeorge on 2007-03-24
I have tried to install 6.06 0n second hard drive after using partition magic to make a linux swap and ex 2 logical partition.
I have added this to boot magic.
When booting the Ubuntu disc will not install.
I have made the D: drive active.
I cannot get sbm.bin onto a floppy disc as the file size is too large for a floppy.
I am trying to use the CD.
After booting into my linux partition with boot magic I just get a message loading Ubuntu.
It does not load however.
I am using the Ubuntu not the Ubuntu Alternate disc.
I mentioned sbm.bin as I needed this to get the disc to boot on an old laptop.
I have 576 mb Ram.
Pentium 111.
I am putting onto a 10 GB partition on a 120GB drive.
This is my D: Drive.
My C: Drive is only a 10GB drive but I keep this for my 98SE Os with all the software and drivers for that OS.
Any Ideas?

---

### Post by bodhi.zazen on 2007-03-24
> **StGeorge said:**
> I have tried to install 6.06 0n second hard drive after using partition magic to make a linux swap and ex 2 logical partition.

<clip>

Any Ideas?

Yes, sometimes partition magic has compatibility problems.

Use partition magic and delete all partitions (on your second HD)

Leave the 2nd hard drive unpartitioned and as free space.

Boot the Ubuntu CD and partition with gparted, the partitioner on the Desktop CD.

If that fails fall back to cfdisk : 

[http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html](http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html)

If that fails, start a new thread so others can see a new question ;)

---

### Post by msfisher on 2007-03-25
Well, Bohdi, good news and bad news.  I tried the alternate 6.10 CD, rather than trying to fake out Ubiquity.  Ubuntu loaded just fine (YAY, THANKS!) exactly where I wanted it, but during the installation I didn't see a screen to enter a user, just a password.  I probably just missed the dialog for it, but now I can't log in.  What is the default user name?  admin?  Or is there a different startup that I can use to access the user file?   I've been poking around rather than asking you, but haven't had any success and you've been so helpful...  

Also, I didn't see the choice between LILO & Grub, so Grub loaded and now Xandros doesn't load correctly. I know, I should list the whole problem, however I MIGHT be able to fix that -- Xandros has a "fix installation" option in its maintenance menu.  It goes into a verbose/text mode and stops with a "kernel panic - not syncing: VFS: unable to mount root file system on unknown-block (0,0)" statement.  Just when I had my hopes up.

As before, thanks for your help and patience.  Hopefully, as in the line from the Holy Grail "I'm getting better...

---

### Post by msfisher on 2007-03-25
Accidental double post.

---

### Post by msfisher on 2007-03-25
I just read the post from St. George.  The three partitions I have on my hdb were originally set up by Partition Magic!  Granted, the ReiserFS at hdb2 & hdb3 were reformatted by Xandros, but the whole setup stemmed from PM.  I wonder if that could have been the root of the problem, beyond a bug in Ubiquity.

---

### Post by StGeorge on 2007-03-27
The problem I have is that my first Drive C: with Win 98Se is only a 10GB disc.
I keep this disc for program and System files for Win 98SE and all the Software.
I partitioned C: for Ubuntu but I only have 2GB spare for Ubuntu 6.06.
It installed there but I need a bigger Partition for it.
On my D: Drive which is a 120GB disc I moved up the Fat 32 section and created free space at the beginning and set it active.
On this drive I have 90GB of files, music etc for windows so I do not want to format the whole drive.
I partitioned the drive at the beginning and gave space of 9GB for the Linux Ext 3 and created an extended partion of 1GB for swap space.
I ghosted my Ubuntu into that drive and tried a repair on it but cannot get it up and running.
I tried to install into that space but cannot do it.
I have used Partition Magic 8 for the partitioning and used boot magic to point the os's.
I have used Norton Ghost to Ghost Ubuntu on C: to the space I created on D:
I can see the files on D: I have ghosted on the Ubuntu install on C:
I wondered if I could correct those files to boot D: Ubuntu from C:
Any ideas would be welcome.

---

### Post by bodhi.zazen on 2007-03-27
> **StGeorge said:**
> The problem I have is that my first Drive C: with Win 98Se is only a 10GB disc.
I keep this disc for program and System files for Win 98SE and all the Software.
I partitioned C: for Ubuntu but I only have 2GB spare for Ubuntu 6.06.
It installed there but I need a bigger Partition for it.

2 Gb is too small or /root (for Ubuntu desktop).

> On my D: Drive which is a 120GB disc I moved up the Fat 32 section and created free space at the beginning and set it active.
On this drive I have 90GB of files, music etc for windows so I do not want to format the whole drive.
I partitioned the drive at the beginning and gave space of 9GB for the Linux Ext 3 and created an extended partion of 1GB for swap space.

So far, so good ..

> I ghosted my Ubuntu into that drive and tried a repair on it but cannot get it up and running.

No, that will not work. The 2 gb space is full and the install is incomplete. I do not know of a way to "repair" this, just re-install ..

> I tried to install into that space but cannot do it.
I have used Partition Magic 8 for the partitioning and used boot magic to point the os's.

Still using partition magic ? why ?

With partition magic delete the partitions you made for Ubuntu.

Boot the Ubuntu desktop CD.

Use Gparted to make your partitions for Ubuntu.

Install Ubuntu.

> I have used Norton Ghost to Ghost Ubuntu on C: to the space I created on D:
I can see the files on D: I have ghosted on the Ubuntu install on C:
I wondered if I could correct those files to boot D: Ubuntu from C:
Any ideas would be welcome.

You should be able to configure the MBR of C: to boot Ubuntu. I am not familiar with boot magic.

My advice is to install Grub (or LILO) into the MBR of C: (/dev/hda). The Ubutnu CD will do this if you let it. Grub is the default boot loader and so why not use it ?

What makes you think you can boot or repair an OS that is half installed ? Sure you have some files there on D: but you do not have a compete OS.

Easier to re-install as I outlined above.

How to install Ubuntu : [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by StGeorge on 2007-03-27
OK bodhi.zazen.
I will take your advice and wipe the partitions I have made on D: and make it free space.
All except the Fat 32.
I will try later and post back with the results as I am downloading 6.10 at the moment.
Thanks.

---

### Post by msfisher on 2007-04-09
I should have posted this several days ago.  The solution turned out to be installation using the Alternate CD.  I must have made one error, though because I couldn't log in after the install.  Turned out that there is a default/temporary login built into the Alternate -- "oem".  Once I used that, things were OK.  I've since had other problems, but this one got solved.  Thanks to bohdi.zazen and all those who responded.

---

### Post by StGeorge on 2007-06-22
Just to let everyone know that I installed 6.06 Successfully on the beginning of my D: Drive.
The mistake I made was that I formatted the beginning of my D: Drive with Partition Magiic for a Linux System.
I shouldn't have bothered as the Installation disk does this for you. Just format it as free space with no designated OS type.
So to be brief if you are installing Ubuntu onto a second hard drive format the drive first making sure that the free space is at the beginning. I gave it 10 GB for Ubuntu. the other 110GB is kept for file storing which can be accessed from Ubuntu and Windows. As already stated the first hard drive, C:, I keep my Winblows 98SE and related software, it is only a 10GB hard drive anyway.

---

### Post by StGeorge on 2007-06-22
Footnote:
I installed successfully with the 6.06 Live Disc.

---

### Post by bodhi.zazen on 2007-06-22
> **StGeorge said:**
> Footnote:
I installed successfully with the 6.06 Live Disc.

Awesome :)

Welcome to Ubuntu.

---

