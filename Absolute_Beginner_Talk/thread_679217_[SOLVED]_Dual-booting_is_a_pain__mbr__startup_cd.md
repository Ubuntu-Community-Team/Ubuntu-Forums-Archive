---
title: "[SOLVED] Dual-booting is a pain ? mbr / startup cd"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by willubunto on 2008-01-26
It's easy to find peolple crying in foruns across the net about their mbr being craped after dual windows/linux ins/unistall. Some say its stupid to dual boot and recommend using linux at a propietary machine. Others say no problem dual booting as long as each know what thei'r doing and create the right tools to recover if some goes wrong. One being to backup the mbr before installing linux.
In my case, I would like to be still more safe. 
I would like to install ubuntu in a way that the install would never mass up, in any way, with my xp mbr. Is this possible?
I wonder yes, in case it would be possible to create a start up cd or usb stick, to boot to the partition where ubuntu is installed. Not a start up diskette, as i'm not using it for long.
Does this tool exist, or is there a easy way to create it ?

---

### Post by gruss on 2008-01-26
If your doing this in a desktop then the safest way would be to install a new hardrive and install Ubuntu to that drive leaving windows both physically and logically untouched, then installing GRUB to a boot floppy or thumb drive.
All that being said I've been dual booting systems for over 10 years and never had any issue with any OS's boot loader.  I've used the OS2 one, some other seperate prog lilo and now grub and they've never caused me harm.  Just recently I put dapper on an old system with windows 2000 on it and re partitioned the HD in the d630 and installed alongside XPpro and no issues for me with GRUB

---

### Post by Irihapeti on 2008-01-26
I believe you can use the Super Grub Disk to directly boot Ubuntu without having Grub installed.

There's also a program called (I believe) EasyBCD. It's a Windows program which then allows you to load Linux. The MBR doesn't need to be modified.

---

### Post by The Cog on 2008-01-26
If you really want to try Linux, I reckon dual boot is the way to go. Anything that takes extra effort will mean that Linux will go unused. Installing dual-boot does carry a small risk of mistakes, power cuts halfway through etc, so you should have a backup. But you should have one anyway - if you haven't then make one right now, before a power supply failure or a burglar takes out your hard disk.

---

### Post by erfahren on 2008-01-26
The real reason there are people "crying in forums across the net" about the MBR after ununstalling Linux is because they don't bother learning about it a little first. Even if the Linux partition is just deleted (and GRUB along with it) it isn't very difficult to fix afterwards (especially in WinXP - Vista may be a different story).

Truth is, it's possible for the MBR to get broken in other ways. The WinXP install disk provides a simple way to fix it.

It is good you looked into it first - prevents you from a little frustration later on, but if you are prepared ahead of time it's really not a big deal. If you restore the MBR before the Linux partition is deleted (while you can still boot into Windows) it's really quite easy.

see: [hermanzone's Uninstall (Linux) page](http://www.users.bigpond.net.au/hermanzone/p18.htm) - there's lots of other good information on dual-booting as well there. The site talks about using the Ubuntu AlternateCD (text based installer) but much of the information is still applicable to dual-booting with Linux in general.

---

### Post by willubunto on 2008-01-26
gruss 
*"If your doing this in a desktop then the safest way would be to install a new hardrive and install Ubuntu to that drive leaving windows both physically and logically untouched, then installing GRUB to a boot floppy or thumb drive."*

Thanks Gruss
It's a good suggestion I may try later, but unfortunatlly I haven't a separate hd, right now.


Irihapeti 
[I]"I believe you can use the Super Grub Disk to directly boot Ubuntu without having Grub installed.
There's also a program called (I believe) EasyBCD. It's a Windows program which then allows you to load Linux. The MBR doesn't need to be modified."[/I]

Thanks for the information, Ill gather more info on those two applications


The Cog 
*"...you should have a backup. But you should have one anyway - if you haven't then make one right now, before a power supply failure or a burglar takes out your hard disk"*

:) sure I have, all is possible, thanks.



erfahren
*"...they don't bother learning about it a little first"*

They may not in most cases. That's the reason why I'm trying to collect as much info as possible before going away
Thanks for the other information you provided, I'll get some learn on it, most I wasn't aware about.

In fact, at the moment I'm prepared to run some risks. All personal data is baked up, have done a recent fresh xp install, leaving two untouched partitions for the linux experiences. Also, at the moment I'have some spare time for investigation and learning linux.

The idea of a cd/usb stick for a dual boot seems to me that would make life easear for the sake of piece of mind for many new comers. I would suggest a nice program to be developed by the community and made available in a sticky at this forum.

---

### Post by gruss on 2008-01-27
No problem, glad I could actually help...and erfahren's correct too.  fixing these issues are actually easy in most cases.  I remember not long ago if you had another OS and installed windows it would disable the boot the flag on that partition.  Many Many people thought it "broke" their install when about 15 seconds in fdisk would re-enable it ;)  Just make a plan and you'll be fine, there are many ways to "fix" these things.

---

