---
title: "I'm a Ubuntu Newb w/ questions"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by mrdeeno on 2006-12-23
Hi everybody.  I am an old/new Linux user and interested [again] in Linux, particularly Ubuntu, at the suggestion of a coworker of mine who uses it for EVERYTHING except Autocad and Solidworks.

He gave me the v.6.06 CD and I tried it out from the CD and like it. 

A little history:  
About 10 years ago (late high school/early college years), I experimented with Linux, but this was before it advanced as far as it has. I had it installed and was using it off and on with my Windoze, but the software support wasn't there yet (and I didn't have broadband yet, so it really sucked).  And some of the computer programs I used in school were only Unix based, so I have some experience with that.   But since graduating college and starting work, I've been mainly on Windoze based machines, until my colleague told me about Ubuntu.

It seems like Linux has come a long way from when I first experienced it, and with broadband internet, things are much easier (both for apps and support).  

I have a couple questions before I go ahead with the install:

1) When I installed Linux on my old laptop 10 years ago (forgot what distribution...it wasn't a popular one), I had the boot menu to choose between windoze or linux.  When I switched to Windoze totally, the boot menu still came up, even though I uninstalled Linux.  

Will I have the same problem with Ubuntu in case I decide to uninstall it?  And what is the procedure to uninstall it?  

2) I currently have 2 partitions on my laptop:  C: (20gb) is for my Windoze OS and apps, D:(40gb) is for cache and some backup.  Both are NTFS and the D: (which was intended for documents) is the larger of the 2.  I also have an external USB drive for all my pertinent data that I wouldn't want to lose in case my HD crashes.  What would be the ideal setup for Ubuntu?  I am thinking of resizing the partitions at 30gb each and using the D: partition for Ubuntu...what file system should I use (Fat32?  NTFS? etc.?)

3) I am worried internet access.  I have a Linksys Wireless G WPC54G V3 PMCIA card.  This is important because if I am switching to Ubuntu, I will probably need a lot of support to start out, and it would be a pain to switch to Windoze and get the info/support I need, then to reboot into Ubuntu to use it.  How easy is it to set up this network card?

Thanks in advance for the responses.  

I know I'll have many more questions once I'm up and running, but I just need to get these clarified before I go for it.

---

### Post by Sef on 2006-12-23
> what file system should I use (Fat32? NTFS? etc.?)

Use the default file system ext3.   FAT32 can be both read and written to by Linux and Windows.  NTFS cannot be written to by Linux, though there are beta drivers for Linux which can.

> Will I have the same problem with Ubuntu in case I decide to uninstall it? And what is the procedure to uninstall it? 

You can overwrite GRUB by using /fixmbr, I believe is the command.

---

### Post by Bachstelze on 2006-12-23
1) No, you will get a nice error instead ;) But it can be fixed pretty easily. Boot from a Win XP CD, go to a recovery console and run *fixmbr*.

2) First, forgot the drive letters-thingie. It's totally a DOS/Windows invention and you won't find it anywhere else. For the partition scheme, it's all up to you. 5 GiB is considered to be more than enough for Ubuntu. The problem will be the NTFS, as it is not - and probably never will be - 100% supported - they're getting close but there are still a few gaps.

3) Search for it in the Wiki, especially [this page](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards).

---

### Post by towsonu2003 on 2006-12-23
> **mrdeeno said:**
> 
1) When I installed Linux on my old laptop 10 years ago (forgot what distribution...it wasn't a popular one), I had the boot menu to choose between windoze or linux.  When I switched to Windoze totally, the boot menu still came up, even though I uninstalled Linux.  

Will I have the same problem with Ubuntu in case I decide to uninstall it?  And what is the procedure to uninstall it?  

yes, because that screen isn't Linux, but something else that gets installed along Linux, namely lilo or grub or what have you (boot loader). 
see [http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458) (ironically)
> 
2) I currently have 2 partitions on my laptop:  C: (20gb) is for my Windoze OS and apps, D:(40gb) is for cache and some backup.  Both are NTFS and the D: (which was intended for documents) is the larger of the 2.  I also have an external USB drive for all my pertinent data that I wouldn't want to lose in case my HD crashes.  What would be the ideal setup for Ubuntu?  I am thinking of resizing the partitions at 30gb each and using the D: partition for Ubuntu...what file system should I use (Fat32?  NTFS? etc.?)

you seem to have 60G total. I would take 10G from them and use it for ubuntu. the filesystem you will want to use is probably ext3. 
pls backup your information before doing anything. than defrag your ntfs partitions a couple of times. and keep in mind: although improbable, you never know what resizing will do... so try to make sure that you will be able to recover if something stupid happens (like C: getting erased)... 
> 
3) I am worried internet access.  I have a Linksys Wireless G WPC54G V3 PMCIA card.  This is important because if I am switching to Ubuntu, I will probably need a lot of support to start out, and it would be a pain to switch to Windoze and get the info/support I need, then to reboot into Ubuntu to use it.  How easy is it to set up this network card?

I think that is broadcom... see [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?highlight=%28WifiDocs%2FDriver%29)
Try doing that stuff using the LiveCD, without installing. that would give you an idea on whether it will work or not...

See here for other documentation on installation: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by LameBMX on 2006-12-23
The live CD concept is great ... gives you the opportunity to test what will work (especially with hardware) before you have to wait for a proper install .... printer first :) .. then when you find out what makes your hardware work properly ... print out the directions you followed ... and when you have all your devices down pat commit ubuntu to the harddrive

---

### Post by Tomosaur on 2006-12-23
Don't forget that you will also need to create a swap partition alongside your ext3 partition. I think the general rule is half your RAM size, but there's a whole load of guides floating around which should givey ou a more accurate figure.

---

### Post by mrdeeno on 2006-12-23
THanks for all the responses.  

I think what i'll do is resize my partitions (with partition magic) so my C: partition is 40GB and use the 20gb partition for Ubuntu.  I don't have anything to back up since I migrated all my data to the external drive and only use the HDD for my windoze apps, all of which can be reinstalled anyway.

another question I have is Blackberry support.  I don't have the Blackberry desktop software installed because I only use it to transfer files to it as a removable drive (Blackberry 8100 with 2gig).  Would Ubuntu recognize this as another removable drive as Windoze does?

---

### Post by Sef on 2006-12-23
> I think what i'll do is resize my partitions (with partition magic)

It's best not to use Partition Magic.  It and Linux do not always get along.  What I would recommend is using [GParted]("http://gparted.sourceforge.net").   There is no cost for it.   It is the partitioner on Ubuntu.

---

### Post by mrdeeno on 2006-12-24
Ok, I'm having trouble already with the install which I hope is something I"m overlooking...

I have my hard drives partitioned so my Windoze partition is 40gb and 20gb is left over.

I ran Ubuntu from the CD and tried the install.  I made a new 2gb partition from the 20gb of free space for a swap partition and the remaining for the Ubuntu partition.  

But when it gets to the window for selection of where to mount which partition, I don't have an option for the swap partition.  The new 2gb partition was created with Linux-swap format, but after I hit the apply button and it goes to the next screen, it doesn't see it.  When i go back, it labels the partition as "unknown". 

I tried it again and it still does the same.  What is wrong?

---

### Post by mrdeeno on 2006-12-24
Ok I figured it out. 

I had to exit the install and go to the partition app instead and it setup the swap partition for me and it saw it during the installation.

---

### Post by LameBMX on 2006-12-24
tons of means to the same ends ..

---

