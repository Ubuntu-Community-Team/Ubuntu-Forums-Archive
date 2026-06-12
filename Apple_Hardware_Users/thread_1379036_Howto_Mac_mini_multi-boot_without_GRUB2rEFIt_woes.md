---
title: "Howto: Mac mini multi-boot without GRUB2/rEFIt woes"
date: 2010-01-12
forum: Apple Hardware Users
---

### Post by Yako no Kai on 2010-01-12
In trying to set up a triple-boot OS X/Karmic/XP setup on my 2009 mac mini, I encountered some (but not all) of the problems in [this thread]("http://ubuntuforums.org/showthread.php?t=1297229") and many others.  I found that if you don't take special precautions, Karmic will easily render both your Ubuntu installation and your Windows installation (if you have one) unbootable.

The problem here is essentially that every piece of software in the installation chain is broken in some way or lacks some piece of critical functionality.  There are many holes and if you step in one, you'll have to go back to start. It may be possible to get installed in the normal fashion if you have enough days to spare, but I spent many hours following the steps in that thread and others only to replace my original problem with others, then restore the original.  I wanted to have Linux installed before February so I chose to avoid, rather than fix, the broken bits.

This post contains few troubleshooting phases ('run this command and see if it fixes the problem') but does require you do do a few things that will seem insane.  I'll try to explain why, without getting too tangential.  I'm not entirely sure that I'll manage, so forgive me if I ramble too much.

**The Rogues Gallery**

Each of these pieces of software is culpable in some way.  Whenever you use one of these programs, keep the bugs in mind and simply don't use whatever is broken.  One of the other pieces of software will pick up the slack.

[LIST]
[*]OS X Disk Utility
[*]rEFIt ([http://refit.sourceforge.net](http://refit.sourceforge.net))
[*]GRUB (specifically version 1.97 beta, IIRC)
[*]Ubuntu Installer/GParted
[*]Windows XP Installer
[/LIST]

GRUB and GParted are most broken here.  Be extra careful when dealing with them.  GRUB2, in particular, is horrendously broken.  It *will* hose your disk, and it's up to you to decide if you are up to the task of searching the forums and fixing it.

**Partition notes**

Only the first three partitions you see in Disk Utility will be part of the MBR disk.  MBR supports four primary partitions, but there is a tiny partition at the beginning of the disk which Disk Utility is hiding from you.  So you only have three.

On an EFI disk, you cannot create extended partitions, but you can create more than four primary partitions.  Windows won't be able to see partitions after the fourth one, but Ubuntu can see them all.  Put your Ubuntu root (or /boot if you like it that way) on partition 3 and if you need more, you can add them at the end.  Dozens of howtos on the internet say that if you are installing Windows, install it on partition 4.  Remember, in Disk Utility this will look like 2 and 3.

**The EFI Dance**

Just get used to doing this series of steps every time you make a change to a partition, format something, or install an operating system.  Keep in mind that the Ubuntu LiveCD won't be able to reboot.

1. Shutdown.
2. Start up.
3. In rEFIt, select the partition tool.  If asked to synchronize the disks, say 'y.'  Be on the lookout for 'Unknown' appearing in the MBR.  If it does, you did something wrong and will need to fix it/start over.
4. Boot into OS X.  A rEFIt script in the startup does some magic to 'bless' the disk.
5. Shutdown.
6. Start up.

**Installation steps**

The main thing to do here is avoid GRUB2.  After reading that, if you are upgrading, Ubuntu will not replace the original GRUB with GRUB2, I realized that the way to get Karmic installed is to start with Jaunty.  Jaunty (9.04) is the latest version of the installer than uses the original GRUB, and you will need that if you want an easy mac install.

1. In OS X Disk Utility, shrink the OS X partition and create partitions for Ubuntu and/or Windows.  These new partitions should be ms-dos (FAT32).

_Notes_

[INDENT]In my experience, any of the following will cause rEFIt to be unable to properly sync the disk.  One of the partitions showed up as 'Unknown' if I did one of these: Creating a partition with Ubuntu installer/GParted, formatting a partition as FAT32 in GParted, formatting a partition AS NTFS in GParted.  The only solution when this happens is to delete the partition and start over with Disk Utility.[/INDENT]

[INDENT]rEFIt can only sync very clean, well-behaved data.  When hit with the output of GParted (which I suspect is invalid but am not qualified to say for sure), it can't deal with it and chokes.  But Disk Utility is fine.  It can reliably create and resize partitions that rEFIt will be happy with.  I never had any problems with it.  Always create your partitions with Disk Utility.[/INDENT]

[INDENT]On the other hand, Disk Utility can only create or format HFS+ and FAT32 partitions.  It also wastes ~128MB of space after each HFS+ partition (but not after FAT32 partitions), so always create FAT32 partitions.[/INDENT]

[INDENT]Disk Utility cannot reliably delete NTFS or ext3 partitions, or partitions that show up as Unknown in rEFIt.  Sometimes it refuses to look at the disk, sometimes it errors out but will work if you retry, and sometimes it completely crashes.  I found it safer to delete, but not create, partitions with the Ubuntu LiveCD.[/INDENT]

[INDENT]FAT32 partitions created are not bootable after a Windows install, so you *must* get the Windows installer to format the partition.[/INDENT]

2. Do the EFI Dance.

3. Boot the Ubuntu live CD and format the partitions you want for linux.  According to various forums, rEFIt doesn't support ext4, so it is probably safest to stick with ext3.  Your call.

_Notes_

[INDENT]When installing Windows, there will be only one FAT32 partition to choose, which makes it impossible to miss.  When installing Ubuntu, all you will need to do is select your already-formatted ext3 partitions.[/INDENT]

[INDENT]GParted can format partitions as ext3 (I can't confirm swap; with 4GB of RAM, I don't need it; might eventually have a small swap file).  It also doesn't have problems with deleting partitions.[/INDENT]

4. EFI Dance.

*(Windows XP steps, not needed if you don't triple boot).*
5. (Optional, depending on installer version) Fill up the FAT32 partition with files.  Leave as few megs as possible.

_Notes_

[INDENT]XP cannot create partitions on a GPT/MBR disk, and it will not install on an existing partition formatted as NTFS (by GParted, at least).  If you install on a FAT32 partition created by Disk Utility, it won't boot, so you must get XP to format.[/INDENT]

[INDENT]Depending on the specific type of XP you are installing (apparently), it might not give you the option to format.  But if leave so little free space on the drive that Windows will be forced to format it, then you'll get the option to format.[/INDENT]

6. Put the XP CD in and restart.  Hold down 'C' when restarting.  When XP says to press any key too boot from CD, press a key.

7. Select the FAT32 partition.  You will be asked to reformat it.  Do so.

8. When it reboots, hold down 'C' when restarting.  When XP says to press any key too boot from CD, DON'T.  Just wait.

9. After this phase of install it will reboot again.  Hold down 'C' when restarting.  When XP says to press any key too boot from CD, DON'T.  Just wait.

10. When XP starts up, remove the XP disk and put in the OS X DVD.  Install the Apple hardware drivers.

11.  EFI Dance.  After the dance, you should be able to boot XP through rEFIt and by holding down Alt when booting.  It worked for me three times, and once I did the dance, everything was OK.  You'll want to verify windows with Microsoft.
*(End Windows XP steps)*

12. Boot Ubuntu Jaunty (9.04) with either the alternate installer iso or the mini iso.  

_Notes_

[INDENT]The Karmic installer installed GRUB2 against my wishes and hosed my disk.  It wasn't an optional choice.  It wasn't the default choice.  It was the *only* choice.  Totally irresponsible.  Installing GRUB2 will most likely be the last thing you do before deleting all your MBR partitions and starting over.[/INDENT]

[INDENT]Also, rEFIt hasn't been updated since March of 2009, so it won't recognize GRUB2 either.  It will just be a 'legacy disk.'[/INDENT]

[INDENT]Jaunty won't install GRUB2, not having it.  The theory with a minimal installation is that it means less stuff that can break on upgrade.  Personally, I used the mini ISO and unetbootin.[/INDENT]

13. When you get to the partitioning stage, select your existing partitions, which you formatted in step 3, select the proper type of disk and mount them.  At minimum, mount / and /swap (if you're using it).

14. When you get to GRUB, install it to either the MBR or to the Ubuntu partition.  Personally, I chose to install to /sda, so that is the only method I can personally confirm.  There is a down side to this: after you do this, you will get the grub menu on both the Linux and Windows menu entries in rEFIt.  

I can't confirm that it works with /sda3, but most of the howtos on the net recommend it.

_Notes_

[INDENT]The only minus to installing GRUB on the MBR is cosmetic.  You have two menus that do the same thing.  It also takes several seconds longer to boot into Windows.[/INDENT]

[INDENT]But this works for me.  It works even when you skip rEFIt entirely, by holding down Alt when starting up.  There is no Linux option here, but if you select Windows, you still get to boot Linux.  You might even be able to get rid of rEFIT entirely, should you choose.[/INDENT]

15. Do the EFI dance.  I *think* this is the last time.

At this point, I was able to boot into Ubuntu.  I had my functional triple boot system.  I only got as far as step 15 once, but I don't see much in steps 12-15 that could go wrong.  Perhaps where you install GRUB, but everything did exactly what I expected it to do.

16. ```
 sudo do-release-upgrade 
```

17. Reboot.  Now you are in Karmic Koala.

18. ```
 sudo apt-get install ubuntu-desktop 
```

There is no reason why kubuntu-desktop or xubuntu-desktop wouldn't work just as well.

19. Reboot.  Now you are in a normal Ubuntu login.

20. You will still be able to connect to the internet, but won't be able to edit the connection settings for this setting in gnome or kde network managers. This seems to be caused by the upgrade.  It's a very old bug that still hasn't been fixed.

```
 gksu gedit /etc/network/interfaces 
```

Under 'auto eth0' will be a line starting with iface.  Comment it out or delete it, save, and reboot.  Then delete the auto eth0 connection in gnome network manager.

21. Find your device under [CategoryMac]("https://help.ubuntu.com/community/CategoryMac") and finish any extra hardware steps.  For the Mac Mini 3.1, I have one thing to add.  If you add _reboot=pci_ to your boot options, I can confirm that rebooting will work.


**Summary**

Ubuntu on the mac mini is like Satan's own jan-ken-pon game. Fixing problems caused by other developers has been my job for a decade, so I was sort of used to it, but it was still painful.  Ubuntu made XP unbootable twice, forcing me to start over, but it seems to be functional now and running nicely.

---

### Post by linuxopjemac on 2010-01-12
It shows again that installation of Ubuntu on an Intel Mac is not as straightforward as many people might think. I hope the developers pick this up and make Lucid Lynx install a whole lot easier on said machines.

---

### Post by jamesey on 2010-01-12
it seems like this could all be fixed if the rEFIt and Grub people could take a day to chat.

---

### Post by phawnex on 2010-01-13
my install went almost flawless, had a short bug with my sound and wireless card. but they were resolved within 2 days. not it runs and operates with no real problem.

(running an imac 24" dual-booting with ubuntu 9.10)


i was planning on purchasing a macmini in the future, does it really give that many problems in the installation process?

*hasnt really messed or heard with macmini's  / linux issues so i wouldnt know.

---

### Post by eumel on 2011-03-10
I did a triple boot install on my macmini (mid 2006 with Core2Duo) yesterday without any major problems.

The most annoying thing for me was that you can't boot from usb.

My steps were the following:

[LIST=1]
[*]Resize mac partition and create partitions for every system either unformated or with fat
[*]Install reEFIt
[*]Synchonize MBR with EFI parition data
[*]Boot Win7 from DVD and install it to partition 3 (as mentiond in post above)
[*]Boot kubuntu 11.04 alpha 3, install to partition 4 and i've set grub to plant in partition 4, not mbr
[/LIST]



Everything went fine exept Win7 dont has every drivers for sound, powerindicaters and a usb device. But thats no problem for me till I may only use it for few software from university.

Now in reEFIt I get three boot entries, firstly macosx, secondly win7 and thirdly linux which loads grub and then kubuntu.

I installed everything in 32bit exept MacOSX.

Now I enjoy 3 OS on one mini device with big screen :popcorn:

---

