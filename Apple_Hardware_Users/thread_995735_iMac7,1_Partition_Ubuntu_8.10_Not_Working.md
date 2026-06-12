---
title: "iMac7,1 Partition Ubuntu 8.10 Not Working"
date: 2008-11-28
forum: Apple Hardware Users
---

### Post by Stasven on 2008-11-28
Machine: iMac7,1
Operating System: OS X Leopard

Hi there, I'm wanting to install Ubuntu 8.10 (I made a CD) onto a partitioned part of my Macintosh HDD but I'm not sure how I should format it. I used to have XP running off of an NTFS partition but I removed it so I could install Ubuntu. I've read online to just boot up from the Ubuntu CD and follow instructions for partition but I'd like some more opinions if possible.

My impatience has had the better of me once again. I set up a "Windows" partition via BootCamp (60GB, FAT32 I presume) and then booted up from Ubuntu disk (strangely labelled as "Windows"). It all seemed to be working well, and I reset the computer. I then held down the Option key to switch to the Ubuntu HDD partition and the only recognised drive was the Macintosh. 

I checked Disk Utility and there are two new drives, that are grey-ed out: "Linux Swap" and "disk0s4" as partitions of my internal drive. 

I don't know what to do now. Disk Utility says that out of my "298.1 GB WDC WD3200AAJS-40RYA0 Media" internal HDD are my drives: Macintosh (236.9 GB); Ubuntu [BootCamp Partition] (124.5 MB); DISK0S4 (58.3 GB); and Linux Swap (2.5 GB).

How can I just make it work as two simple partitions; one for Macintosh, one for Ubuntu?  I'd really appreciate any help. :confused:

---

### Post by pxwpxw on 2008-11-28
That partition info from Disk Utiliity looks passable. Mac names for partitions can be a bit confusing. 
The booting problem happens because the ubuntu installer destroys the MBR partition table it needs to reboot.
You need to have rEFIt and run the refit partition sync tool to sync (gptsync) the GPT/MBR tables. That will renew the MBR partition table.

---

### Post by Stasven on 2008-11-28
Okay thanks, I'll try that.

Edit: I don't understand how to use that programme.

---

### Post by pxwpxw on 2008-11-28
> **Stasven said:**
> Okay thanks, I'll try that.

Edit: I don't understand how to use that programme.

Right, its very well explained on the refit site -

The rEFIt Project
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

And there is more general help in the forum here 
Sticky:    Apple Intel Users FAQ  (Multi-page thread 1 2 3 ... Last Page)
[http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393)

Before You Post
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by Stasven on 2008-11-28
> **pxwpxw said:**
> Right, its very well explained on the refit site -

The rEFIt Project
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

And there is more general help in the forum here 
Sticky:    Apple Intel Users FAQ  (Multi-page thread 1 2 3 ... Last Page)
[http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393)

Before You Post
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

Yeah I've read the F.A.Q.s and the information on Mac installation but I've still somehow managed to screw it up. :/ I want to consult someone in person but I highly doubt I'd find someone around here that would know about doing this. My main concern right now is just restoring my HDD to a single partition instead of 6; 5 of which are empty on unusable.

---

### Post by pxwpxw on 2008-11-29
Do you mean you just want 1 system = ubuntu on the computer?
(not an idea I would recomend).

---

### Post by Stasven on 2008-11-29
> **pxwpxw said:**
> Do you mean you just want 1 system = ubuntu on the computer?
(not an idea I would recomend).

Right now I want to restore my HDD to one single partition; run by Mac OS 10.5. Once I'm able to do that I want to try and set up a partition for Ubuntu 8.10.

---

### Post by pxwpxw on 2008-11-29
Thats clear.
Get a terminal open in macosx.
Get this info
```

$ sudo diskutil list
$ sudo gpt -r show /dev/disk0

```
post it here.
That will help explain your options.
I have a 300GB drive with just macosx and  linux. It occupies 4 partitions plus a 124MB space, which is what you have there now as I read it. You cant just have 2 partitions.

---

### Post by cyberdork33 on 2008-11-30
boot from your leopard install disc and start DiskUtility you can delete the second partition there.

Once you do that, you can install very easily using this methid:
[http://ubuntuforums.org/showpost.php?p=6211925&postcount=2](http://ubuntuforums.org/showpost.php?p=6211925&postcount=2)

---

### Post by Stasven on 2008-11-30
> **pxwpxw said:**
> Thats clear.
Get a terminal open in macosx.
Get this info
```

$ sudo diskutil list
$ sudo gpt -r show /dev/disk0

```
post it here.
That will help explain your options.
I have a 300GB drive with just macosx and  linux. It occupies 4 partitions plus a 124MB space, which is what you have there now as I read it. You cant just have 2 partitions.

I began to type that but I got a warning from Terminal to not do it unless necessary; so I'd like a second opinion if possible.

> **cyberdork33 said:**
> boot from your leopard install disc and start DiskUtility you can delete the second partition there.

Once you do that, you can install very easily using this methid:
[http://ubuntuforums.org/showpost.php?p=6211925&postcount=2](http://ubuntuforums.org/showpost.php?p=6211925&postcount=2)

I tried using DiskUtility; both from Leopard and from the Install Disc.

I appreciate the effort, but this hasn't helped at all so far. :(

---

### Post by cyberdork33 on 2008-11-30
> **Stasven said:**
> I began to type that but I got a warning from Terminal to not do it unless necessary; so I'd like a second opinion if possible.All it does is get information about the state of your disc. It is safe. The tool can do other things and that is why there is a warning.

> **Stasven said:**
> I tried using DiskUtility; both from Leopard and from the Install Disc.

I appreciate the effort, but this hasn't helped at all so far. :(
Since you already have the OSX partition down to the size you need, you really don't need to repartition anymore. just boot the Ubuntu LiveCD, and use the partitioneditor application to delete the extra partititions after the hfs+ partittion (the osx partition). Then you can start the installer and tell it to use the free space as I outlined in thelinked post.

---

