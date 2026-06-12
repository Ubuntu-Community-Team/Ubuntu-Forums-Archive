---
title: "uninstalling ubuntu partition on power book G4"
date: 2007-07-18
forum: Apple PPC Users
---

### Post by devonatron on 2007-07-18
What's the safe way to go about doing this? Is there anything i need to know re: yaboot? Will i also be able to reclaim the deleted ubuntu partition for mac os x? Any help would be greatly appreciated.

D

---

### Post by crgcole on 2007-07-19
Q & A - 

Are you trying to completely remove Ubuntu? Extend the extra free space to Mac partition? Reinstall OSX?

 I'm running a dual boot on a mac Mini --- why r u getting rid of Ubuntu ?

C.

---

### Post by devonatron on 2007-07-19
yes, yes, and dindnt want to have to reinstall macosx if i don't have to.

Well for starters my display doesnt work properly (although at first it did) with ubuntu and yaboot doesn't even ask me if i want "x" for osx or "l" for ubuntu. Well, maybe it does but i can't see it on my display, so i just keep hitting x when the screen sorta flickers. Ubuntu was a fun experiment for a while but now i just rather hand that extra space back over to osx.

Thanks. If there is already a howto dedicated to this feel free to point me in that direction.

D

---

### Post by Auria on 2007-07-19
to get rid of yaboot you can just go in the OS X pref pane and select the OS X partition as default boot, yabooy shouldn't annoy you anymore then.

as for removing the partition... i think resizing back HFS partitions up is unsupported by the ubuntu partitioner but i might be wrong. you might use an OS X partition tool (though you'll need to buy them)

the easiest way would be to reformat the ubuntu partition from OS X in disk utility, you'll still have 2 partitions but both of them accessible to OS X

---

### Post by guidop on 2007-07-22
Since you can't seem to get to OSX using yaboot, try this:
- Power On, or Restart while holding down the "option" key, wait for it to finish scanning for bootable disks, and select your OSX partition to boot.
- In OSX, go to System Preferences -- Startup Disk, and select your OSX partition.
- Restart to verify it works.


Once you have that working, you have two ways to reformat your Linux partition as HFS+

Easy way, but leaves an 800 kB hidden boot partition with yaboot on it:
- Go to Utilities -- Disk Utility, select the Linux partitions(s), which are sort of grayed out, and Erase them, formatting for Mac OS.

More involved, but brings all your Linux partitons back to a single partition, assuming you started that way:
- Boot Ubuntu (or other Linux) install CD.
- Go until given the choice to Partition Manually
- Delete all of your Linux Partitions (most likely ext3 and boot), should now have free space.
- Format the free space as ext2 or ext3 (or anything, doesn't really matter.
- Write the changes to disk
- Abort the installation
- Restart into OSX, and use Disk Utility as above.

---

### Post by ivesjd on 2007-08-03
What you can do, is format all the space from linux as Fat32 or NTFS and make sure it is one partition. Then boot into OS X and startup bootcamp. You should now be able to restore the disk back to how it was before.

---

### Post by devonatron on 2007-09-04
> **guidop said:**
> Since you can't seem to get to OSX using yaboot, try this:
- Power On, or Restart while holding down the "option" key, wait for it to finish scanning for bootable disks, and select your OSX partition to boot.
- In OSX, go to System Preferences -- Startup Disk, and select your OSX partition.
- Restart to verify it works.


Once you have that working, you have two ways to reformat your Linux partition as HFS+

Easy way, but leaves an 800 kB hidden boot partition with yaboot on it:
- Go to Utilities -- Disk Utility, select the Linux partitions(s), which are sort of grayed out, and Erase them, formatting for Mac OS.

More involved, but brings all your Linux partitons back to a single partition, assuming you started that way:
- Boot Ubuntu (or other Linux) install CD.
- Go until given the choice to Partition Manually
- Delete all of your Linux Partitions (most likely ext3 and boot), should now have free space.
- Format the free space as ext2 or ext3 (or anything, doesn't really matter.
- Write the changes to disk
- Abort the installation
- Restart into OSX, and use Disk Utility as above.

I did the more involved option. When I go to erase the partition in Mac OS X disk utility I get the following error "A disk with a mount point is required".

Did I skip a step?

D

---

### Post by Afishionado on 2007-09-05
parted can resize HFS partitions:
[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)

The links talks about resizing to make room for a new Ubuntu install, but going the other way should work as well.

Sorry to hear Ubuntu didn't work out for you. :(

---

### Post by guidop on 2007-09-05
Oops, sorry for the bad advice above.

Could you try this and see if it works?
(I can't without trashing my ubuntu install.)

- Boot from the Ubuntu install CD, and use the partitioning tool
- Per the suggestion made by _**ivesjd**_, format the ubuntu space as FAT (maybe labeled as MS-DOS or similar).
- Write the changes to disk
- Abort the installation

- Boot into OS X
- Start Disk Utility, select the partition and _see if you can mount it._ 
(There should be a "Mount" button in the disk utility window.)
(Mouse over it, it may be mounted automatically.)

- Then, _see if you can erase and format it as Mac OS extended._

I know that OS 10.4 (PPC and X86 versions) will mount a FAT partition on an external FireWire hard drive, so I think this has a chance of working.   What version of OS X are you using?

This method, if it works, will still leave you with 2 Mac OS formatted partitions, but won't touch  the OS X install.  

If you want to go back to 1 Mac OS partition, you'll have to try the command line OS X diskutil / Linux parted method linked to by _**Afishionado**_, though I'd personally be wary of trying it without backing up my OS X install.
(Once you have one HFS partiion, go back to OS X and run "sudo diskutil enableJournal [volume name]" to re-enable journaling in OS X.)

Please post again when you find something here that works (or doesn't work) for you.   Best of Luck.

---

### Post by devonatron on 2007-09-12
still won't mount. should i be formatting in fat16 or fat32?

---

### Post by devonatron on 2007-09-13
also, tried ntfs and osx disk utility still won't mount the partition.

---

### Post by guidop on 2007-09-16
Well, I tried a number of things on my 12" Powerbook G4, but have found no way to do this non-destructively using just Ubuntu and Mac OS ppc utitlities.

From the Feisty ppc live CD, one can use [gnu] parted to shrink non-journaled hfs+ partitions, but not enlarge them.  Perhaps a later version will fix this issue, I'm still trying to see what the bug status is.

One might be able to use the Mac OS 10.4 ppc version gpt function to create an hfs+ partition from free space without destroying other partitions, but I have not tried it yet.  A trick like this supposedly works on Intel Macs, and the BootCamp assistant can be fooled into joining the two partitions into one.

I did successfully boot from Prosoft Engineering's Drive Genius CD to non-destructively enlarge an hfs+ partition into free space at the end of the partition.  I have v 1.1.5. I think 1.5 is the latest, and it costs about 80 US Dollars.

My suggestion would be to buy an external firewire drive at least big enough to back up your Mac install, and use Carbon Copy Cloner to make a bootable backup, boot OS X from the backup and use Disk Utility to repartition the Mac's harddrive, then use Carbon Copy Cloner to restore your install from the backup.  An 80 GB backup copy took about an hour (each way) when I did it today.  At least when you're done, you'll also have a drive for backups, something one should always have.

---

### Post by bodek on 2007-09-16
I also noticed that gparted from live CD can shrink, but not enlarge hfs+ partition.
My solution was to boot into OSX and in disk utilities make an image of the OSX partition to an external drive (in my case it was an USB drive).
Then boot from OSX install disk, go to disk tools, disk utilities and delete all the partitions creating just one for the 'new' OSX. Then again from the disk utilities you can restore the disk image giving you your mac os in the state it was before, with all software and documents in place. It worked in my case, anyway.
Hope it helps.

---

### Post by ubuntubrian on 2007-09-18
I have the exact opposite desire. I love Ubuntu and have successfully cloned my HD to a new and larger HD via USB, 60GB to 120GB. My Ubuntu partition is filling and I now have a new drive ready to be installed in my laptop with exact copies of the partitons and 56GB of free space that I want to expand my Ubuntu partition into. I can use iPartition but I'd like to do it from the Ubuntu live CD I'm running right now. 
I found this and it explains how to remove journaling from an ext3 formatted partition:
[http://www.hermann-uwe.de/blog/resizing-ext3-partitions-with-parted](http://www.hermann-uwe.de/blog/resizing-ext3-partitions-with-parted)
But I'm wondering if I can do it with Gparted somehow.
I don't mean to hijack this thread but it is so similar!
Thanks

---

