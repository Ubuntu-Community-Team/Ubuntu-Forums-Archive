---
title: "Ubuntu Auto-loads!!!  How to load VISTA???"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Crypto77 on 2007-10-22
Ok well I downloaded the latest iso copy of Gutsy Gibbon from my Windows Vista machine and burned it to a disk.  Let it be noted I am a first time Linux user. 

So anyways I booted from the disk and proceeded to setup an installation.  I had a single partition at the time and decided to make two new ones -  20 gigs of my 160 gig hardrive (50 were free at the time) for the main files (with a mount point of "/") and 1 gig for the "swap" partition.  I just checked by re-loading from the live cd and it says that the rest of the space is in a partition called "free space."  Well after having a nightmare trying to connect to my wireless internet, I decided that I needed to get my Windows wifi card driver.  

So I shutdown and attempt to re-boot and load Vista.  Well, the bios page loads and the - BAM the grub loader begins and about 1 second later Ubuntu is loading.  I have no option to choose which system to load, it simply loads automatically.  I have a bad feeling that I may have wiped the original partition containing all 110 gigs of my VISTA data.  Any help to calm my nerves down???  Currently I am wishing I had always stayed with Macs- someone please prove me otherwise.

---

### Post by cfaulkner on 2007-10-22
Install in order...

1> Vista
2> Linux

Install Vista and create the partition you want and leave the rest blank, after you're done, install Ubuntu and install that, make sure the Grub boot loader is setup and then you should be right as rain.

---

### Post by LanDan on 2007-10-22
after the BAAMMMM and before ubuntu loading can you do hit the Esc button?

---

### Post by cfaulkner on 2007-10-22
also, on some systems you can Hit F12 on BIOS screen to go to a Boot Device area.  Your system maybe different.  Also try changing the boot order to CD/DVD first.

but on that note, posting what kinda system you have would help a little there.

---

### Post by scheuri on 2007-10-22
I am sorry to tell you...

1) ALWAYS BACKUP YOUR DATA WHEN DOING STUFF* LIKE THIS!!!!!!!!!!!
2) ALWAYS BACKUP YOUR DATA WHEN DOING STUFF* LIKE THIS!!!!!!!!!!!
3) ALWAYS BACKUP YOUR DATA WHEN DOING STUFF* LIKE THIS!!!!!!!!!!!
4) ALWAYS BACKUP YOUR DATA WHEN DOING STUFF* LIKE THIS!!!!!!!!!!!
5) Linux is not Windows, so DO NOT EXPECT IT to behave like Windows
6) I am actually quite wondering why GRUB did not recognize your windows-partition, but since I havent used windows for years as dual boot I am unable to say why.

7) FREE space on a hard disk is NOT what you need to install linux! You need UNALLOCATED space.
I am sorry, if you are talking about the right thing, but since you are new to linux I have to assume you are talking about the wrong stuf here.
Free space is, probably in your sense, usually what you have left on a existing partition (like 50 GB on d:/). But Linux can not use that as it is already "used" in a exisiting parition! Vista may use those 50 GB for data or whatever, but you can not install anything in it.
So, what you need is unallocated space on your harddrive which is not yet part of a partition. The Installer of Ubuntu will see that unallocated space and you are able to install Ubuntu in that space without (usually) harming everything else...but still point 1 to 4 applies!

What you need to do now is firing up Gutsy, open a terminal or console and type "fdisk -l /dev/sda" or "fdisk -l /dev/hda" in it.
Tell us what it says...so we might help you or at least answer your question.

Good luck
Stefan





* Upgrading your system from release to release, installing Ubuntu, repartioning, etc.


So, you can boot into gutsy?
Great...

---

### Post by Gio-van-I on 2007-10-22
reinstalling is a lot of work.

I would try to find out if you still have vista on your hard drive. All partitions are loaded in Gutsy so you should be able to find the one Vista is installed on if it still exists.
Just open your file browser and check all the partitions between the floppy drive and the recycle bin.

If it still is there just modify your grub load list: 'sudo /boot/grub/menu.lst'.
Beware! be sure not to edit this file if you don't know how it works. Otherwise you might not be able to boot at all.
But adding windows to the list should cause no problems.
Just add this to the end of the file.
[INDENT]title		Microsoft Windows Vista Ultimate
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/INDENT]
You micht have to change the second zero in the (hd0,0) if windows isn't on your first partition. If it is on the second make it (hd0.1) and so on.
Now save and reboot.

Should this not work You will probably have to reinstall windows.
After you're done make the partition that holds grub active instead of the windows one. Now add windows the same way I described before and you have both running while only having to install windows instead of both again.

I don't know how your HD was partitioned before you created 2 partitions. But I always try to make a image first and writing it to CD so that I can safe everything before I edit my disc, Next to that make sure you're partitions arn't mounted while resizing. Could also cause some problems.

Good luck and keep us posted

---

### Post by Crypto77 on 2007-10-22
> **scheuri said:**
> 
So, what you need is unallocated space on your harddrive which is not yet part of a partition. The Installer of Ubuntu will see that unallocated space and you are able to install Ubuntu in that space without (usually) harming everything else...but still point 1 to 4 applies!

What you need to do now is firing up Gutsy, open a terminal or console and type "fdisk -l /dev/sda" or "fdisk -l /dev/hda" in it.
Tell us what it says...so we might help you or at least answer your question.

Usage: fdisk [-b SSZ] [-u] DISK      Change partition table
            fdisk -L* [-b SSZ] [-u]         List partition table(s)
            fdisk -s PARTITION             Give partition size(s) in blocks
            fdisk -v                                Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b: 2048: (for certain M0 disks) use 2048 byte sectors


*character looks similar to an "L" with a tail at the top too.  My apologies as I am having to type all of what I see from another computer as I cannot get on the internet yet from the Ubuntu infused machine.

---

### Post by Crypto77 on 2007-10-22
> **LanDan said:**
> after the BAAMMMM and before ubuntu loading can you do hit the Esc button?
Ok I pressed escape twice right when I knew the grubloader was about to commence and get a window that says "
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+

---

### Post by LanDan on 2007-10-22
> **Crypto77 said:**
> Ok I pressed escape twice right when I knew the grubloader was about to commence and get a window that says "
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+

OK, nothing bad yet

what you do now is 1 st follow crypto77 advice and the giovanni's

with a bit of luck you will be jumping the ceiling from happiness in a few minutes

---

### Post by dpar on 2007-10-22
I got a bad feeling here........
 What you want to type in the terminal, when you get there is > sudo fdisk -l
Thats a small L.

---

### Post by Crypto77 on 2007-10-22
> **LanDan said:**
> OK, nothing bad yet

what you do now is 1 st follow crypto77 advice and the giovanni's

with a bit of luck you will be jumping the ceiling from happiness in a few minutes
Ok I am slightly confused - "follow crypto77 advice"?  Follow my own advice?  What advice - I don't feel qualified to offer myself advice yet.  :)   Hopefully I get this worked out soon though.

---

### Post by LanDan on 2007-10-22
that would be

sudo fdisk -l

---

### Post by Gio-van-I on 2007-10-22
Well crypto77, how did it go?

If you still don't know what to do let us guide you step by step.
First start with typing this in a terminal:
[INDENT]sudo fdisk -l[/INDENT]
This will return a list with which partitions are on your disc.

If we know which there are we can tell you on which windows should be located. And if windows is still in working order we'll show how you can add it to your Grub load list.

---

### Post by Crypto77 on 2007-10-22
"
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16005 * 512 = 8225280 bytes
Disk identifier: 8x77334625

Device Boot        Start           End          Blocks               Id        System
/dev/sda1  *              I         2432      19535008+          83       Linux
/dev/sda2           2433         2554      979965                 82       Linux swap/Solaris

"

And yes - I am lost as to what the next step for me to do would be.

---

### Post by Martje_001 on 2007-10-22
> **Crypto77 said:**
> "
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16005 * 512 = 8225280 bytes
Disk identifier: 8x77334625
 
Device Boot Start End Blocks Id System
/dev/sda1 * I 2432 19535008+ 83 Linux
/dev/sda2 2433 2554 979965 82 Linux swap/Solaris
 
"
 
And yes - I am lost as to what the next step for me to do would be.
I'm afraid you deleted you Windows Vista partition. Reinstall Vista and then install ubuntu and make sure you install it on a seperate partition!

---

### Post by LanDan on 2007-10-22
> **Martje_001 said:**
> I'm afraid you deleted you Windows Vista partition. Reinstall Vista and then install ubuntu and make sure you install it on a seperate partition!

yup, i hesitated for a second to bring his news......but its gone

---

### Post by Bob Bismal on 2007-10-22
I used [ this apcmag guide ]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first") it's pretty much the same for 7.10.  At the bottom it tells you how to set it up to boot windows or Ubuntu.  Hope it helps.

---

### Post by Crypto77 on 2007-10-22
Hehe - yep I am not surprised at all.  As soon as I realized I wasn't allowed to boot into Vista I had a feeling that the Vista partition was gone especially after re-checking and being unable to find any info on the Vista partition.  

Thank God I still have this trusty old G4 mac that houses all important files.  The Vista machine was built by myself as an attempt to familiarize myself more (yuck) with the Windows world and to toy around with.  I am looking to change that with Ubuntu as a longtime lover of UNIX based operating systems, I am hoping to gradually transfer most of my stuff over to Ubuntu and try the Linux route.

---

