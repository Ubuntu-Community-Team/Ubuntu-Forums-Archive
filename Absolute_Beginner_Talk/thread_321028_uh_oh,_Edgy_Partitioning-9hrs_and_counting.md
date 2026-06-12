---
title: "uh oh, Edgy Partitioning-9hrs and counting"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Trajan47 on 2006-12-18
A bit of advice/help may be needed for a total newbie.

I went through the edgy installation process late last night.  I am looking to do a dual-boot with my Windows XP. On the partition disks step, I chose to Resize IDE1 master and use freed space.  After setting the limit for the new partition (80%, 56GB was the minimum the slider would allow me), i clicked continue.  Now, 9 hours later the partitioning still hasn't completed.

So, any advice on what i should do?  The mouse icon is still spinning, so maybe its just working through it, but i have my doubts.  If I do cancel installation and retry it, do I lose everything on the comp'?  What options do I have?  What awful things may have already happened to my drive and data? :confused: 

I did clean up and defrag my hard drive before i started the install.  I put some of my computer specs underneath if it helps.

Gateway Laptop
80GB Hard drive-17GBs were totally free pre-installation
Windows XP, NTFS Files-Sys
Athlon XP-M 

Thanks so much, from all the threads Ive read in the past few days the people in this forum seem great.

---

### Post by hal10000 on 2006-12-18
Usually partitioning and resizing lasts only a few seconds (max. 1 minute).
So either something went wrong or (dont' laugh, it happened to me more than one time) there is somewhere on your desktop a dialog box which wants to get yout ok but is covered by another window so you can't see it.
If this is not the case, then you should post at which state (exactly) it is hanging. If it has not partitioned anything then you have good chances by aborting the installation and start again. 
In a terminal window do [COLOR="Red"]sudo fdisk -l[/COLOR]
If the partitions on your harddrive have not changed, then you can safely abort the installation. If you can't abort by clicking the button then do [COLOR="Red"]  <ALT>+<F2> xkill[/COLOR] and point with your mouse to the window you want to kill, but first try to stop it by using the button.

If partitioning has already begun then you might have a problem.

---

### Post by Trajan47 on 2006-12-18
Thanks for your reply!
I aborted the partitioning and installation process.  Luckily for me it didnt even begin the partitioning, it must have froze up and the mouse icon just continued rotating.  Either way I am defragging my drive a couple more times for good measure and then giving it another shot.  

Quick Question:
In the partitioning step for Edgy Eft, when i select the 1st option (Resize IDE1 master and use freed space).  The slider bar sets the minimum size of my new partition at 80% (54GBs or so) of my 80 GB drive.  I was hoping to make it share 50/50 with windows.  Is this slider bar limit normal or a risk to my Windows OS?
Odd question i know, but it took me by surprise, none of the guides or books mentioned that.

Thanks again!

---

### Post by hal10000 on 2006-12-18
To answer your quick question I have to know how your harddrive is partitioned and how much of your windows partition is used.
You can post the outputs of [COLOR="Red"]sudo fdisk -l [/COLOR] and mount your windows partition and then post the output of [COLOR="Red"]df -h[/COLOR]

---

### Post by Trajan47 on 2006-12-18
Ok, im new to this so let me know if im even giving you the relevant info.

Right now I know my drive has only one NTFS partition that takes up pretty much the entire drive (75.43GB).  About 16 GB of that is free space.  So far i'm on my fourth defrag (through windows) of my drive.

I wasnt sure how to handle your instructions for sudo fdisk or mounting the partition. sorry, haha

Thanks

---

### Post by hal10000 on 2006-12-18
If there is about 16GB free space on the windows-partition, you can only resize up to that point, but this shold be enough space for ubuntu.
Try to start the installation again (i guess there are six steps). Be sure you have not mounted the windows partition. In a terminal window type: [COLOR="Red"]mount[/COLOR] and if the output shows that windows is mounted, you first have to unmount it: [COLOR="Red"]sudo umount -a[/COLOR]

Good luck

btw, the commands I mentioned above can be executed in a terminal window (I guess in gnome it's under menu--->system--->terminal (or xterm). I'm using KDE, so I'm not familiar with the gnome menus). The output can be marked with mouse and pasted with the middle mouse button into an editor (or somewhere else).

---

### Post by d3v1ant_0n3 on 2006-12-18
> **hal10000 said:**
> 
btw, the commands I mentioned above can be executed in a terminal window (I guess in gnome it's under menu--->system--->terminal (or xterm). I'm using KDE, so I'm not familiar with the gnome menus). The output can be marked with mouse and pasted with the middle mouse button into an editor (or somewhere else).


In Ubuntu, the terminal can be found at Applications>Accesories>Terminal

---

### Post by Trajan47 on 2006-12-18
Ok, ive given it another try.

Generally, what happens is after selecting a partition size and clicking forward, the mouse icon spins but nothing happens.  Several times after clicking forward the mouse starts spinning and the buttons 'fade-out' but it soon returns to the same screen with the same settings, when i click forward again, no luck.  The system simply spins away, no progress bar, nothing.  

Ive played around with the sizes of my new partition and the smallest one 13GB (18% or so) leads to the same place.  The mouse spins but nothing happens.  It ran for all of last night to no avail.

I tried the terminal commands but it didnt change anything.  All a bit puzzling really.  

Im running the install off a Ubuntu 6.10 Live Disc, on a Gateway laptop, Windows XP, 80GB HD - NTFS. 

Would appreciate any help.  Im itching to get playing with Ubuntu.

Thanks

---

### Post by AgenT on 2006-12-18
You may have hardware problems. For example, your hard drive may have an extensive amount of bad blocks that are not hidden by the hard drive firmware.

A quick way to check if you have visible bad blocks is to start up a LiveCD and in a terminal type:
```
sudo badblocks -v /dev/hdaX
```Where hdaX is a partition you want to check. Check all of them. To find out your partition list, type:
```
sudo fdisk -l /dev/hdX
``` Where hdX is every hard drive.  Your first hard drive will probably be hda, thus you would type sudo fdisk -l /dev/hda

Check all partitions that begin show up with fdisk. Your main partition will usually be hda1. Each check should last about 5-10 minutes.

Also, listen to your hard drive. Does it sound strange? Does it make noises that usually do not happen? Is it louder than normal?

What are your computer specifications? It may be that the graphical installer is having problems with your hardware. If that is the case you can install via the Alternate CD. Note that the Alternate CD is not as newbie friendly as the LiveCD.

---

### Post by Sef on 2006-12-18
> What are your computer specifications? It may be that the graphical installer is having problems with your hardware. If that is the case you can install via the Alternate CD. Note that the Alternate CD is not as newbie friendly as the LiveCD.

The alternate installer is mostly just some additional typing.  Not hard to do.  Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") to see how to install from the alternate cd.

---

### Post by smoker on 2006-12-18
> **Trajan47 said:**
> 
Right now I know my drive has only one NTFS partition that takes up pretty much the entire drive (75.43GB).  About 16 GB of that is free space. 

i think lack of free space may be your problem here. windows tends to need at least 10-15% free space on it's partition to operate efficiently. plus, you are giving the partitioner very little room for manouvure resizing your windows files into a much more compact space.

if you can, i would uninstall any windows apps/games, etc, you haven't used for three months or more, and move all the data you can to a backup cd/dvd to make more space in the windows partition. once this is done, clean up the drive of temp/log/junk files, and switch off system restore (this will delete all restore points which take up space), then defrag again, and turn system restore back on.

it is always wise to back up all crucial data before a resizing a partition, though i think the chances of anything going disasterously wrong is remote.

hope this helps:D

---

### Post by susiekins on 2006-12-26
I had the same problem you had, it froze at the same point after doing the same things. I previously had an Ubuntu installation that I had removed by deleting the partition. But, on going back and deleting that other linux-swap partition, it no longer gets stuck there, and is now installing. =) I don't know if this will help you at all, maybe if you have some other partition thats interfering. Maybe. Just putting it out there.

---

