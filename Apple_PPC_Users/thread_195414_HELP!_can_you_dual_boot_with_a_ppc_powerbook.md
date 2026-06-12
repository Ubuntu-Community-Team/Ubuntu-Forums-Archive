---
title: "HELP! can you dual boot with a ppc powerbook"
date: 2006-06-12
forum: Apple PPC Users
---

### Post by zalberico on 2006-06-12
I have a Power PC Pwerbook and was wondering if you can dual boot with it.  I burned a copy of ubuntu (the desktop non permenant version) using disk utility  and now I don't know what to do.  How do you start it up?  If you use it will it wipe out your hd.  Any help would be fantastic thanks.
                                            zman14321

---

### Post by projectle on 2006-06-12
Here is what you must do...

Back up your OS X Data.
Delete your OS X Partition.
Create a new "New World Boot Partition" (through the Ubuntu CD)
Create a new OS X partition of whatever desired size (through the Ubuntu CD)
Create a new Linux partition of whatever desired size (through the Ubuntu CD)
Create a new Swap partition of 2x your total ram (through the Ubuntu CD)
Install OS X onto the OS X partition
Install Ubuntu onto the Linux Partition.

After the installation is completed, press "L" to boot to Linux, "X" to boot to OS X, "C" to boot to CD.

Restore your data.

Also, in the future you may want to look at doing a full size Ubuntu Partition and then use MOL for OS X, setting it to run on VC-8 so that you can "CTRL-OPT-F7" or  "CTRL-OPT-F8" to swap between simultaneously running Linux and Mac.

---

### Post by tidris on 2006-06-12
[QUOTE=zman14321]I have a Power PC Pwerbook and was wondering if you can dual boot with it.  I burned a copy of ubuntu (the desktop non permenant version) using disk utility  and now I don't know what to do.  How do you start it up?  If you use it will it wipe out your hd.  Any help would be fantastic thanks.
                                            zman14321[/QUOTE]
You should be able to dual boot OSX and LINUX. I am doing that on my Pismo G3 Powerbook. It is easier to do if the powerbook is a newer "new world" model. What Powerbook model is it? How big is the hard disk in it?

With the live desktop CD, holding the C key while rebooting should get Ubuntu running directly from the CD without the hard disk being affected in any way.

---

### Post by zalberico on 2006-06-12
Thank you! I have a very new powerbook model running panther right before tiger came out.  I'll try to boot up off the disk, how do you partition a drive delete the mac os partition, back up the os and configure dual boot.  I know am asking a lot, I'm new to linux thanks for all your help

---

### Post by zalberico on 2006-06-12
I just used ubuntu off of the live cd and it worked great! The only thing was that it didn't see my wireless network.  How do you set that up?

---

### Post by tidris on 2006-06-12
[QUOTE=zman14321]Thank you! I have a very new powerbook model running panther right before tiger came out.  I'll try to boot up off the disk, how do you partition a drive delete the mac os partition, back up the os and configure dual boot.  I know am asking a lot, I'm new to linux thanks for all your help[/QUOTE]
There is more than one way to do all that, but this is how I did it:
1- Backed up the internal hard disk to my external Firewire hard disk. My external Firewire disk is an exact copy of the internal disk and I can boot OSX from it if I need to.
2- Created free space for Ubuntu in the internal hard disk. I did that by booting from the external Firewire disk and using the OSX DiskUtility to reduce the size of the OSX partition in the internal hard disk. In my Powerbook I created 6 GB of free space and that left 10 GB for OSX. There is a 16 GB disk in my Powerbook.
3- Restored OSX from the Firewire disk to the reduced size OSX partition in the internal hard disk.
4- Booted from the live desktop CD and clicked the Install icon in the Ubuntu desktop. I allowed the Ubuntu installer to automatically create all the needed  partitions in the free disk space I had created previously. I didn't have to create by hand any of the partitions needed by Ubuntu, not even the Apple_Bootstrap one. As for the dual boot, the installer automatically configures it for you if it finds OSX installed in the disk! 
5- Assuming everything goes well, after rebooting you get a textual menu that allows you to select between LINUX, OSX, or CD.

---

### Post by EuroCity on 2006-06-13
Yes, the "backup, resize and restore" option is certainly the easiest one in order to reinstall OS X after having made some free space for Linux.

Also, remember that, when installing OS X, Disk Utility always creates a 128 MB free space partition (invisible from within OS X and Disk Utility itself, but visible from the Ubuntu installer) at the beginning of the disk (and also between different HFS+ partitions, for that matter): that's why the bootstrap partition can be created so easily by the Linux installer, taking 1 MB of those free 128 MB immediately after the partition map itself; similarly, if a separate /boot partition is needed (see the old iMacs and G3 towers, for example), the remaining 127 MB of those pre-allocated 128 MB could be used for that one - always without interfering with the existing OS X partition(s).

Maybe the reason Apple decided to make those apparently useless 128 MB free space partitions was also to make installing Linux easier? Or were they intended for future file system features? Who knows...

---

### Post by zalberico on 2006-06-13
I backed up some important things on my ipod, but now I don't know how to partition my drive when I open disk utility it says this disk contains the boot volume and cannot be partitioned.  I have a 20 gig ipod and cannot therefore put everything on my 60 gig computer hd onto it.  Do I need to buy a program to partition my computer?
                                                                Thanks

---

### Post by tidris on 2006-06-13
[QUOTE=zman14321]I backed up some important things on my ipod, but now I don't know how to partition my drive when I open disk utility it says this disk contains the boot volume and cannot be partitioned.  I have a 20 gig ipod and cannot therefore put everything on my 60 gig computer hd onto it.  Do I need to buy a program to partition my computer?
                                                                Thanks[/QUOTE]
The disk you are booted from can't be partitioned because partitioning wipes out the disk contents. Anything you haven't backed up will be gone for good. So after partitioning you have to reinstall or restore OSX and all your personal data files back into the disk. You can boot from the OSX CD, then run DiskUtility from there. 

I didn't use the OSX CD because my Firewire disk has OSX in it and that allowed me to boot from it.

---

### Post by Ptero-4 on 2006-06-13
It's said that the partitioner in the ubuntu 5.10 install CD (not sure about the 6.06 one, probably the alternate version have this) can non-destructivelly resize your OS X partition as long as you disable journaling in it before resizing it.

---

### Post by sleestak on 2006-06-19
I have been beating my head for days on this...I have a B&W 450 G3  w/20GB SCSI that I am trying to get set up as a dual boot.

These are the steps I took:

1- partitioned drive w/ disc utility on OSX CD.  First partion= freespace, second for OSX
2- Install OSX
3-Install Ubuntu 6 (also tried 5) on largest free space avail.

Install goes fine till I have to reboot, then I get a flashing mac folder for a minute...then into YaBoot and press "L" boots up OSX

Also tried just wiping out entire HD with Ubuntu CD and installing just linux...same result but yaboot wont load linux and it just sits there with a folder icon.

So far I am not too stoked on this....anyone encounter these issues?  

I have read that putting the boot partition first makes this go easier, but how the hell do you do that when apple keeps slamming its 32.3kb partition right up front?!!

---

### Post by rottenmac on 2006-06-29
Same here. I restart or start with the ALT key down, so i can choose what to start with.

Then it comes with l for linux.
then i get the same screen as when I hold down the ALT, except the graphics are not right. (Pixely and some inverted colors.)

I installed everything, then used the sudo command and in Terminal installed automatix and let it do its thing. (Not everything installed , but it seemed to do most of it.)

Now I would really like to use Ubuntu, but there really needs to be a complete NOOB guide to installing and all.

Anyone ???

---

### Post by ifishfortorque on 2006-06-29
I'm no pro at yaboot.  I messed around with it a good deal, though, 'cause I was running Ubuntu, Gentoo and OS X on the same powerbook (G4 1.5GHz).  I also don't know anything about automatix . . . 'fraid I might not be able to tell you much.  However:

I have the boot partition as /dev/hda2, and I was able to install yaboot to it without anything going crazy on me (my main problem was forgetting to sudo).  If you're having problems, do some reading on yaboot.conf and make sure it's adjusted as it should be.  Things might be a little different with SCSI disks, but you can find a couple of tips [ here]("http://www.gentoo.org/doc/en/handbook/handbook-ppc64.xml?part=1&chap=10#manual_yaboot") and [ here]("http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch6.en.shtml").  I don't know whether you've tried this, but try doing your partitioning with mac-fdisk rather than with Apple's Disk Utility.  Install Ubuntu first, maybe?  I borrowed my sister's iPod for a few days and backed up my OS X data to that, then wiped the disk clean, did partitioning with mac-fdisk, installed Gentoo, then Ubuntu, and then finally OS X.  

I'm under OS X now, but when I'm back using Ubuntu I'll poke around in the Powerguts of the Powerbook and post again with more details.  Sorry I'm not much help at the moment.  

Also, regarding a question someone asked earlier on, the wireless isn't detected and autoconfigured by Ubuntu yet if you've got an Airport Extreme.  You have to do a little work on your own to get it going.  See [here]("http://ubuntuforums.org/showthread.php?t=185174") and [here]("http://ubuntuforums.org/showthread.php?t=142727") for more details.  

Matt

---

### Post by ifishfortorque on 2006-06-30
Righto, the yaboot.conf:

```

boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=5
root=/dev/hda5
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda4
defaultos=macosx

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash"

```

note in particular the first line.  Apple does their silly thing first, but when you run sudo ybin -b /dev/hda2, it _should_ sort of override it.  

I got these lines from the Ubuntu installer and let it update them, but I originally installed yaboot during installation of Gentoo.  

Hope this helps.

Also, zman & ptero: I dunno as I'd trust resizing an hfsplus partition . . . but since you're making a backup anyway, you might as well try it.

---

### Post by ubuntubrian on 2006-07-01
I would advise 2 things for zman14321:
Stay with the Live CD for awhile and see how you do. I f you really like it you can move on to-
You do not need to destroy your OS X partition or lose the data on it. Creating a bootable backup is great, I have one that I never use. There are a couple threads in theis forum that demonstrate how to partition your HD without destroying data but I used the proprietary iPartition. I followed the instructions to the letter and I lost no data and have a perfectly great dual boot set up that only has problems when I create them. I was a total noob when I did the set up but I had been using Fink ported UNIX/LINUX and X11 on OS X. It's a good alternative and no need for any partitioning or anything like that. Of course I want a totally FOSS platform and did the Ubuntu Warty install. It's daunting but doable-just be very careful and BACKUP.

---

### Post by mokelvey on 2006-08-24
> **projectle said:**
> Here is what you must do...

[COLOR="Red"][COLOR="Black"]Back up your OS X Data.
Delete your OS X Partition.
[COLOR="Red"][/COLOR][/COLOR]Create a new "New World Boot Partition" (through the Ubuntu CD)
Create a new OS X partition of whatever desired size (through the Ubuntu CD)
Create a new Linux partition of whatever desired size (through the Ubuntu CD)
[/COLOR]Create a new Swap partition of 2x your total ram (through the Ubuntu CD)
Install OS X onto the OS X partition
Install Ubuntu onto the Linux Partition.

After the installation is completed, press "L" to boot to Linux, "X" to boot to OS X, "C" to boot to CD.

Restore your data.

Also, in the future you may want to look at doing a full size Ubuntu Partition and then use MOL for OS X, setting it to run on VC-8 so that you can "CTRL-OPT-F7" or  "CTRL-OPT-F8" to swap between simultaneously running Linux and Mac.

I followed this plan as best I could but was stumped when it came to the parts in RED above. I could not deduce from the obscure (to me) labeling which partition format of the remaining 10 would produce a "New World boot partition". Most of the partition labels were meaningless to me in light of your above-quoted plan. One choice for OS X partition was greyed out, so I chose hfs formatting. I could not deduce from the obscure labeling which partition format of the remaining 10 would produce a "Linux partition". The Linux swap partition was plainly labled, according to your above plan. 

The installation attempt, probably my 20th, was unsuccessful, for no reason I could make use of. 

The major steps of your plan were tempting and easy. The details were obscure and defeating to one who does not know what ext3, ext2, jfs, reiser4, reiserfs, ntfs nor xfs signify. Nor could I Google these terms nor find a meaningful reference in the manual or on the forums.

This is the kind of thing that is so discouraging about installing ubuntu.
mok

---

### Post by mokelvey on 2006-08-24
> **projectle said:**
> Here is what you must do...

Back up your OS X Data.
Delete your OS X Partition.
[COLOR="Red"]Create a new "New World Boot Partition" (through the Ubuntu CD)[/COLOR]
Create a new OS X partition of whatever desired size (through the Ubuntu CD)
[COLOR="red"]Create a new Linux partition of whatever desired size (through the Ubuntu CD)[/COLOR]
Create a new Swap partition of 2x your total ram (through the Ubuntu CD)
Install OS X onto the OS X partition
Install Ubuntu onto the Linux Partition.

After the installation is completed, press "L" to boot to Linux, "X" to boot to OS X, "C" to boot to CD.

Restore your data.

Also, in the future you may want to look at doing a full size Ubuntu Partition and then use MOL for OS X, setting it to run on VC-8 so that you can "CTRL-OPT-F7" or  "CTRL-OPT-F8" to swap between simultaneously running Linux and Mac.

> **tidris said:**
> There is more than one way to do all that, but this is how I did it:
1- Backed up the internal hard disk to my external Firewire hard disk. My external Firewire disk is an exact copy of the internal disk and I can boot OSX from it if I need to.
2- Created free space for Ubuntu in the internal hard disk. I did that by booting from the external Firewire disk and using the OSX DiskUtility to reduce the size of the OSX partition in the internal hard disk. In my Powerbook I created 6 GB of free space and that left 10 GB for OSX. There is a 16 GB disk in my Powerbook.
3- Restored OSX from the Firewire disk to the reduced size OSX partition in the internal hard disk.
4- Booted from the live desktop CD and clicked the Install icon in the Ubuntu desktop. [COLOR="red"]I allowed the Ubuntu installer to automatically create all the needed  partitions in the free disk space I had created previously. I didn't have to create by hand any of the partitions needed by Ubuntu, not even the Apple_Bootstrap one. As for the dual boot, the installer automatically configures it for you if it finds OSX installed in the disk! 
5- Assuming everything goes well, after rebooting you get a textual menu that allows you to select between LINUX, OSX, or CD.[/COLOR]

For me - the parts in red above were meaningless, because I do not understand what all the little formatting options mean when using the first method: I understand from hfs, hfs+, fat16, fat32, and linuxswap - the rest is so far, undiscoverable after consulting manuals, Google, and the forum. 

The second method didn't work because after I booted ubuntu for possibly the 20th time, the installer refused to do anything automatically with the partitioning, which brought me to my 21st dead halt.

I can play with the live disc boot all I want, have left it running for days, even sent email to myself and participated in the forums from those live CD boots - I just can't get ubuntu to install. I have downloaded and burned 4 different ubuntu CDs. It may be that the burns are imperfect (I can't get ubuntu to install on an Intel Mac nor an i86 XP VM partition either), so I am waiting for the free CDs. before I try anymore of this heart-rending, painstaking frustration. ubuntu should be usuable by the people. I am a person. ubuntu may kill me.

---

