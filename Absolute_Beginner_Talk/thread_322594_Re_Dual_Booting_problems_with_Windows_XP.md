---
title: "Re: Dual Booting problems with Windows XP"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by Mike_cog on 2006-12-20
I have just installed Ubuntu for the first time (using now). I installed on a win XP partition and when i try to log onto XP it starts up then stops. I have followed the comments made and it shows my partitions and that XP is hidden but dont know how to make it active and if i make it active then reboot into Xp will i still be able to boot onto Ubuntu or will it keep going to the active (XP). When i go into disc manager it says it is active. Can you help? Ta

Moderator's note: The thread being referred to is [this one]("http://ubuntuforums.org/showthread.php?p=1905690#post1905690").

---

### Post by ingo on 2006-12-22
So you tried

sudo fdisk -l

and your xp partition is hidden. To make it active download and burn this [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) and the rest should be self-explanatory. If still in doubt contact hop-along from the other thread. He's been through it already :)

---

### Post by VidK on 2006-12-22
When I first attempted a dual-boot and used the manual partition in Ubuntu, it totally effed up Windows and I couldn't boot anymore. Thankfully I backed up my Win stuff. After that... I decided to just reinstall everything using the Partitioning step-by-step instructions at:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I used the last 3rd from the last suggestions (Win-NTFS, Ubuntu-Shared-EXT3, Ubuntu-Root-EXT3, LinuxSwap-EXT3) and used FS-Drive on windows to use the EXT3 Partitions. Everything works great! So great that I'm going to do it again! (not because I like installing OSs but because I want to make larger partitions)

The resizing didn't work for me; it just messed everything up. That's why the whole new partitioning and reinstalling.

~Vid~

---

### Post by Inkpot on 2006-12-22
This is very strange...I have WinXP and Ubuntu dual booted on my system and haven't had any major issues. I don't know the first thing about the ins and outs of installing Ubuntu...I just followed the prompts and used the manual partition thingamajigger. 

/shuts up for fear of sounding like a complete moron who doesn't know what the heck he's talking about....oops...too late....damn....




Ink

---

### Post by Taranis17 on 2006-12-22
I too dual boot my laptop with XP and Ubuntu.  No problems thus far.  I did not use the manual partition option, instead just did the automatic way and adjusted the slider to let Ubuntu use 10% of my hard drive for itself.

This is my third install, and my first attempt with anything Linux in about 8 years (since Mandrake 8), so I'm a complete Linux super-n00b. 

If you crash your OS (like I did 3 times getting my 945GM graphics to work), you can follow these steps to do a reinstall of Ubuntu without messing up your windows install:

Go into Windows' disk management and delete the partitions that Ubuntu made (should be two).  You'll then have your C:\ and unallocated space.

Use a windows partition manager program (I use PartitionMagic 8) and redistribute the unallocated (free) space back into your windows partiton.

Reboot and boot off your XP cd.  When prompted to install windows or repair from the console choose "R", then when the console comes up, log into your windows partition.  

Type HELP for a list of commands, but the only two you should need is FIXMBR and FIXBOOT.  Run FIXMBR first, then FIXBOOT.  Once complete, log out and restart your PC.  That should get rid of the grub boot loader (you should boot straight into windows as if Linux was never there.

Then reinstall Ubuntu as before and try, try again!

---

