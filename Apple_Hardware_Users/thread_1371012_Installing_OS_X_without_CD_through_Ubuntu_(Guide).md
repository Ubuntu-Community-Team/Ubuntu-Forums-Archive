---
title: "Installing OS X without CD through Ubuntu (Guide)"
date: 2010-01-02
forum: Apple Hardware Users
---

### Post by pYrO1v1aniac on 2010-01-02
This is something I'd been stuck on for months on end, so now I've successfully done it, I figure I should write this guide, as I was able to find nothing similar online, except references to using OS X to accomplish it through disk utility. To the best of my knowledge there is no reason why this will not work on distros of Linux other than Ubuntu. This could also probably work using a Ubuntu liveCD.
[I]
There are various legitimate reasons for wanting to do it this particular way, maybe you're missing your OS X installation CD (as I was), or you have a Macbook air or a broken DvD drive, or you lack a Dual Layer DvD on which to burn your image. Either way, I'm not a lawyer, deciding on the legal ramifications of it is up to you. Remember that this guide is for an actual Apple mac computer, and no reference to hackintosh or related projects is relevant, and by owning the mac, you should therefore own a license to the OS X software, but don't quote me on it.[/I]

**My setup-**
Macbook Pro 4,1 with 320GB fujitsu SATA harddrive running Ubuntu 9.10.
Also using a Seagate 500GB external harddisk and a Seagate 20GB SATA harddrive cannibalized from an Xbox360.
The ISO was an image of a Mac OS X 10.5.1 install disk.
You will need-
A computer running Ubuntu 9.10. This could be your mac, or another computer.
An external USB or firewire Harddrive with at least 8GB of free space.
An intel macintosh computer with at least 15GB of space.

To begin.
**1)** **Obtain an ISO of Mac OS X**. This can be done by imaging an install disk on another computer and copying the ISO over to Ubuntu, or more dubiously from certain torrents. The most important thing to note is that you don't get a .dmg file. Large .dmg files are nearly impossible to work with in Ubuntu, and most utilities to convert them either fail because the files are too large, or the resulting ISO is corrupt and cannot be booted. There are also hackintosh ISO's floating around, but these are not the genuine article, and are at best, a poor workaround for users of non-apple hardware to use Mac OS X, so for best results, use a real ISO, though these are quite difficult to locate online.

**2) Plug in the USB/firewire disk you intend to install from.** Back up any data you intend to keep.

*2a) This step may be optional* Open a terminal and type.
sudo apt-get install gparted
Then proceed to System->Administration->Gparted
In the menu select Gparted->Devices and select the disk which corresponds to your external drive.
In the menu, then select device, and create partition table.
Press the advanced arrow, and select GPT as the partition table type. This gives the disk a partition table which is bootable with Intel Mac computers. Again, I do this as a 'to be sure' measure. I'm not sure if its totally necessary.

**3) THIS IS THE IMPORTANT PART.**
This part took a long damn time to figure out. I eventually found this on the arch linux wiki after literally months of googling. Open up applications->accessories->terminal and enter this command
_**WARNING. THIS WILL ERASE EVERYTHING ON THE EXTERNAL DISK, REGARDLESS OF PARTITIONING.**_

[INDENT]**_sudo dd bs=8M if=LOCATION OF ISO FILE of=/dev/sdX_**[/INDENT]

Where X is the identifier of the drive. For example /dev/sdb
You can find this identifier in System->Administration->Disk utility by clicking the relevant drive. It will be shown below the name of the drive.
A common mistake is to enter /dev/sdb1. Do not do this. Enter the identifier for the entire drive. /dev/sdb

Entering this command will create a bootable USB image of Mac OS X. This will take some time, but once your terminal shows you@computername:~$ you'll know the command has finished, and you can remove the drive.

**4) Plug the external drive into your mac and power it on. Holding down the option (alt) key.** This will cause the mac to initiate Bootcamp mode. You should see a large orange drive with a USB icon and "Mac OS X Install DvD". You will also see any other bootable operating systems or devices which are connected. Click the drive, and then the small arrow which appears underneath it.

**5) Begin installing Mac OS X.** 
The installer for OS X can be tricky. It only recognizes GPT formatted disks, so you may have to erase your install destination drive. To do this you'll need to go to Utilities->Disk Utility on the top menu of the installer and erase the drive, replacing it with Mac OS X Journalling file system. I'm not sure how a new installation of OS X will take to existing operating systems on the disk, but it's best to have anything you want saved from this disk backed up in advance. Be careful not to erase the disk *from* which you are installing, as this will recognize as an external drive to Disk Utility.

All going well, Mac OS X should install successfully from this drive.

*Note- This guide is a first draft, and may be tidied up/edited.

---

### Post by slooksterpsv on 2010-01-02
Nicely done, when my OS X 10.5 DVD broke and I only had the ISO, I partitioned my drive and imaged the secondary partition with the ISO. I ran the installer, it worked flawlessly.

--The key here is the title of the drive (DVD, CD, HDD) must be Install Mac OS X or Mac OS X Setup or whatever it's called (been a while).

---

