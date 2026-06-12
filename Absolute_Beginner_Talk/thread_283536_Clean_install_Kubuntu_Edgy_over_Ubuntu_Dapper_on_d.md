---
title: "Clean install Kubuntu Edgy over Ubuntu Dapper on dual boot"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by r76 on 2006-10-24
Please forgive my asking, I have searched lots but not found the answer although I'm sure it must be very simple.

I installed Dapper Ubuntu as a dual boot on an XP laptop.  The problem is that I messed around so much to get this to work with my network card, TV card etc. I just want a clean start now I know the apps, drivers and settings I want.  There are no programs, data or settings that I want to keep on the hard disk (other than WinXP of course) - I can reinstall these later in a matter of minutes.

I also want to move up to Edgy at this time (so want rid of all the dapper stuff to avoid conflicts) as I have heard my TV card should work with that.  Furthermore I want to switch to KDE (hence Kubuntu) as all the apps I use seem to be KDE.

I plan to do all this when Edgy final is released so want to prepare now, and want to avoid complicating the GRUB loader, there are already lots more things there than I know what they are!

Thanks in advance
Rich

Setup:
Dell Inspiron 8500 Laptop
(Dell truemobile 1300 802.11g wireless mini-PCI)
partition 1 - /dev/hda1 windows vfat 39MB
partition 2 - /dev/hda2 windows NTFS 12.7GB
partition 5 - /dev/hda5 extended 3 <ubuntu installed here> 5.86GB
swap partition - /dev/hda6 memory swap
partition 7 - /dev/hda7 extended 3 /home 26.4GB
partition 8 - /dev/hda8 windows vfat /docs <shared with windows> 9.5GB

Artec T1 DVB-T USB TV tuner

---

### Post by Bachstelze on 2006-10-24
Just install Edgy over Dapper, nothing else should be needed :)

---

### Post by EddieA on 2006-10-24
Just an Idea:
Your /home partition seems big enough to shrink - why not shrink it make a new partition for Edgy , set Edgy up as you like it while stikl maintaining full use of Dapper, swap, home and docs. Delete Dapper when you are happy to do so,

---

### Post by r76 on 2006-10-29
Thanks!  I did a clean install - I thought that would mean having to format first.  It is as simple as just booting with the downloaded CD in the drive.  Still I'm VERY glad I noted down the partitions I had beforehand so I knew which to format and which to mount where - the more partitions the more complicated!

Edgy is so much faster, my [TV card]("http://www.ubuntuforums.org/showpost.php?p=1684397&postcount=13") and [WiFi]("http://www.ubuntuforums.org/showpost.php?p=1677564&postcount=3") both working great and Sun Java 5.0 (jre1.5.0 needed for [ProjectX]("http://sourceforge.net/projects/project-x") and [FreeGuide]("http://freeguide-tv.sourceforge.net/index.html")) easy to install from add/remove programs!  Only problem is [Opera]("http://www.opera.com/") not being in the repos but the Dapper .deb works great.  Well done and thanks to everyone involved in developing Edgy!

---

### Post by kinematic on 2006-10-29
it does mean you had to format the partition first.
no need to delete partitions,just format and NEVER install one distro over another one....that's just bad computer practice ](*,)

---

