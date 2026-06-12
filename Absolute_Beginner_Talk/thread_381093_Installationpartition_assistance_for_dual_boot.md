---
title: "Installation/partition assistance for dual boot"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by thefoolisme on 2007-03-10
OK, I've been searching through the forums to try to find the answers, but I can't seem to find everything I'm looking for.  I'm trying to set up a dual boot on my laptop with Windows XP, and Ubuntu.  

The laptop has an 80gb hard drive.  It's set up so that the first 40gb is for Windows.  The other 40 I want to set up for Ubuntu.  I've also read that in order for both OS to share document files, etc.  there needs to be a FAT32 partition in there somewhere.   I can't figure out how to set it up.  

Using the psychocats installing guide, I tried to do a manual partition setup, because it seems that if you use the automatic resizer, you can't allow for the FAT32 partition, or at least that was how I read it.  In the manual partition setup I tried to set up the mounts like this (the hda #s are approximate because I don't have the page in front of me):
/windows      40gb   partition 1  hda1  NTFS (windows XP)
/documents  15 gb   logical hda3(FAT32 partition)
/home            7gb   logical hda4 ext3
/                  15 gb  logical hda 5 ext3
swap              2gb   logical hda 6 

I thought I had it figured out, but when I clicked next, I got an error message stating that no Root was selected (or something like that).  I thought "/" was the root.

Would someone mind giving me the suggested partition setup and what I should call it based on the info above?  Please type slowly and clearly as I am a total newbie when it comes to this.  :-)  

Thank you in advance.

---

### Post by Kateikyoushi on 2007-03-10
Indeed / is root, did you tick the reformat partition checkbox next to it ?
In my opinion 2 GB swap is too much and also 15GB for / again a waste if you have a /home partition as well, I would set it up as follows.
8GB for / and 15GB for /home and 1GB for swap.

---

### Post by Crooksey on 2007-03-10
After you made and created the partitions are you sure that your / partition was set to the correct ext3 partition and that it should be formatted?

---

### Post by thefoolisme on 2007-03-10
OK, I made the sizing changes that were suggested.  I went into manual partition and set it up like this:

/windows      39gb      Part1 IDE/ATA1 (primary) [hda1]
/                    8gb      Partition 7 Disc IDE/ATA (logical) [hda7]
swap              1gb      Partition 8 Disc IDE/ATA1 (logical)[hda8]
/home           12gb     Partition 6 DIsc IDE/ATA1 (logical) [hda6]
/documents   15gb     Partition 5 DIsc IDE/ATA1 (logical) [hda5]  (this is the FAT32 partition so I                                                                                                                         can share documents)

"reformat" was checked for /, swap, /home

I got the error message "No Root file system"

I know I'm missing something simple, I just don't know what it is.  Please help.  Thanks.

---

### Post by jezebel on 2007-03-11
I'm not sure I can help, but...

I was doing a manual partition (for the 1st time!) this morning (installing Ubuntu Edgy on a desktop already running XP and already partitioned..)

I wanted to install in the partition of the master hard drive; XP is installed on C. I wanted to be on D...

(Aside: I have a second, slave, drive also installed, but didn't want to put Ubuntu on it in case it couldn't dual boot)...

Anyway, I'm a noob, and can't  recite a lot of the paths, drive names, etc...

BUT -

after some (a lot of!) trial and error, I did the manual partition during install of Ubuntu 6.1.

I got the same error msg that you did; then I tried something new. 

I DELETED the partition that I wanted to install on. (Right click, delete). Then, right click the alloted space (old partition), and create a new partition for the root drive ( I did 15 gigs, though some say 10 is more than enough); I right clicked again on the empty non-alloted space, and created an 800 mb partition for my swap. then I right clicked the unallotted space again and (without resizing) made it a partition that I would later assign to /home for the install. 

I left the drive type (i.e. ntfs, fat32 etc) at the default, which was something like ext3 or whatever. Sorry...

Then, I made sure to remember that partition 2 (15 gig) = root, etc. 

I clicked next, then assigned partitions appropriately, leaving the fourth choice blank.

Then it worked and recognized my root and installed without a problem...

Please let us all  know if this worked for you.

J.

---

### Post by Kateikyoushi on 2007-03-11
Did you set the filesystem for / and /home as ext3 and for swap as swap ?

---

### Post by thefoolisme on 2007-03-11
Yes, I set the file systems up as you mentioned.  I had thought I had done a good thing when I got all the partitions set up before the install, but I just couldn't get it to work.  So last night, I deleted all the premade partitions, and just installed it with the "most available space" option.  It installed, but I don't have windows mounted, or the FAT32 shared documents partition.  I just wanted to make sure it would install.   I'll probably wipe it out again and start over, unless I can figure out how to get the windows files mounted and add a shared FAT32 partition.  Maybe it was my pre-created partitions that it didn't like.  I don't know.  Any information is appreciated.  

Thanks.

---

### Post by thefoolisme on 2007-03-18
I decided to try this again.  I uninstalled Linux, and then attempted to reinstall it.  I wanted to set it up with a dual boot with XP on 1 HDD.  I wanted to be able to mount the windows files, have a home directory, and have a FAT32 partition so I could share files with Windows.  

I tried the deleting and recreating partitions as mentioned in an earlier post, but I still had the same problems.  I tinkered with it some more, and it seems to be installing now.  Here's how I  set it up:
/windows 39gb Part1 IDE/ATA1 (primary) [hda1]
/boot  80mb  ext3
/ 8gb Partition xfs
/home 12gb Partition xfs
swap 1gb Partition  linux-swap
/documents 15gb Partition (this is the FAT32 partition so I can share documents)

If this works, I should have it set up properly, right?  WIth the best of both worlds, since I don't want to delete the XP yet?  WIth everything I've read, having a /home is great because it will always save your settings, and the FAT32 so you can share files with XP.  

If this doesn't work, I'll be back, I'm sure.  I could just throw it on there, but I don't want to regret my partition decisions later.  

With any luck, next stop will be wireless networking  \\:D/

---

