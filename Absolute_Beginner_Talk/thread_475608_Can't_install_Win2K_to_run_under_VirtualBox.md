---
title: "Can't install Win2K to run under VirtualBox"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Midahed on 2007-06-16
I installed VirtualBox 1.4.0 yesterday to run on my Ubuntu 7.04 Feisty 64-bit O/S.  The VirtualBox installation went OK without any major problems.  However, I can't get Windows 2000 to install as a guest O/S.  

The Windows installation boots from the CD OK, and all goes well until the point at which it would format the drive.  The Windows installation stops (having made no progress on the format) saying that it's unable to format the partition and the disk may be damaged.

It makes no difference whether I choose to format as NTFS or FAT.  I've also tried various combinations of fixed and expanding virtual disk sizes, memory, etc, but the result is always the same.

The log file doesn't make a lot of sense, but just before the time of the failure there's a line that says:-

**Guest Log: BIOS: int13_harddisk: function 15, unmapped device for ELDL=81**

This looks like it's something to do with the problem, but I haven't a clue as to what's causing it.

Anyone got Windows 2000 working as a guest O/S on an Ubuntu-based host?

Any ideas would be much appreciated.  Having wasted a day on this I'm getting close to accepting that the only sensible way to have access to my few must-have Windows programs is to have two PCs or put up with having to dual-boot.  So far my experience of the alternatives is nothing but an unreliable PITA. :(

Thanks,

Mike

---

### Post by jimbob on 2007-06-16
Can't really give you a definitive answer but I've installed XP many times under Virtualbox and never run into any problems.

Can you borrow a copy of XP from someone just to see if you can get beyond that point?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Midahed on 2007-06-17
Thanks for the suggestion.  As it happens, that's what I did eventually.  

From the symptoms it looked like it was either a problem with partitioning or formating.  I wanted to try a manual fdisk to see if I could partition the virtual drive but couldn't find a bootable Windows 2000 recovery floppy that still worked after all these years!   In the end I used my XP installation CD just as far as the partitioning and NTFS format.  That worked OK, after which I could install Windows 2000 by telling it to use the existing NTFS filesystem.

In the meantime I'd installed VMware Server to see how that compared.  I think I'll stick with VMware for the moment.  I like the look and feel of VirtualBox, but it has locked-up several times when doing trivial things like opening the Windows control panel or when playing video and sound clips from the BBC website.  I couldn't see any obvious performance differences between VirtualBox and VMware, so for the moment I'll go for the more mature product that installed without problems and, so far, hasn't locked-up at all.

Mike

---

