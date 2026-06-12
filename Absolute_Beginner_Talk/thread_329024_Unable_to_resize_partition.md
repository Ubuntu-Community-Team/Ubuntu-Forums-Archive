---
title: "Unable to resize partition"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by TexasD on 2006-12-31
Good Evening!

I'm looking for a bit of guidance. I appreciate any advice that anyone can give.

I am attempting to install Kubuntu 6.06 LTS onto a Dell Lattitude D620 Laptop. This computer is currently running Windows XP Pro. I am attempting to set this computer up to dual boot.

Before installing, I backed up all important files, and ran defrag from Windows. I then booted off of the live cd.

I chose the option to automatically resize and partition the drive (which, for some reason, shows up as a SCSI drive.) I then get the following error:

"Failed to create enough space for installation"

I did a bit of Googling, and came across this thread: [http://www.ubuntuforums.org/archive/index.php/t-264406.html](http://www.ubuntuforums.org/archive/index.php/t-264406.html)

I fired up QTParted, and it only shows one partition ... so the fix in that thread is a no go.

From QTParted, I got the following error message when attempting to resize:

"Error: opening /dev/sda1 as NTFS failed: Invalid Argument"

Next, I stumbled upon this bug: [https://launchpad.net/distros/ubuntu/+source/partman-auto/+bug/54778](https://launchpad.net/distros/ubuntu/+source/partman-auto/+bug/54778)

Per the information there, I defraged again. Still, nothing.

I then attempted to resize via ntfs-resize. It spit out an error message about /dev/sda1 not being mounted.

Up until this point, I had been using a CD that Canonical sent. Just to be sure, I downloaded an ISO of Ubuntu 6.06 LTD (not Kubuntu), just to rule that out. Same results.

So, yeah ... I am pretty confused. Am I missing something here?

Thanks again, and Happy New Year!

- D

---

### Post by TexasD on 2007-01-01
Quick update:

I just booted off of the GParted live cd, and was given the following error message:

[I]Failed to startup volume: Invalid argument. 

Error(22): Opening '/dev/sda1/' as NTFS failed: Invalid argument
The device does not have a valid NTFS[/I]

Any ideas? I'm pretty much stuck here.

Thanks for the help!

- D

---

### Post by Bartender on 2007-01-01
I hate Dell.  

Not positive about this, but I think what's hanging up Dell owners are the stupid Dell utility and recovery partitions scattered all over the HDD.

I'd sure like to see a definitive answer to this.  Some Dell owners don't seem to have any probs, others delete the extra partitions or get around them in some manner, others such as yourself hit a brick wall.

Good luck, hope you get some help on this!

EDIT:  Did you check the md5 for the GParted download, and burn the CD slowly?

---

### Post by housam on 2007-01-01
Try to use the Partition Magic tool. it is good with ntfs format. 
Also you can check your disk through windows. by typing CHKDSK in the command prompt
If it has a problem , type CHKDSK/F to fix it. and if it is ok try any partition tool for resizing. 
If you got no results, you should give your Dell agent a call.

---

### Post by TexasD on 2007-01-01
Thanks for the suggestions.

More updates:

Attempted to resize partition using Partition Magic. Partition Magic fails when opening. Received the following error: "init failed: error 117. Partition drive letter cannot be identified"

Turned off Windows File Protection, and Dell Quick Restore. Re-defraged. Tried to install Kubuntu - same result.

Ran 'chkdsk /F'. Defraged twice, for good measure. Tried to install Kubuntu - same result.

Ugh. Looks like I hit one of those brick walls.

Thanks again for the help.

- D

---

### Post by Sef on 2007-01-01
> Try to use the Partition Magic tool.

Don't use partition magic.  It and Linux tend not to get along.  Instead use [GParted]("http://gparted.sourceforge.net").  It is an excellent partitioner that works well with Linux and Windows, and the cost is $0.00.

---

### Post by TexasD on 2007-01-01
Thanks for the suggestion ... but I already tried gparted. It can't do anything with the hard drive. Spits out the following error:

"Failed to startup volume: Invalid argument.

Error(22): Opening '/dev/sda1/' as NTFS failed: Invalid argument
The device does not have a valid NTFS"

I tried partition magic based on an earlier suggestion.

At this point, I'm stumped. I really want to install Ubuntu, but I need to have the option to boot into Windows (I need a handful of proprietary Windows-only apps for work.)

Thanks.
- D

---

