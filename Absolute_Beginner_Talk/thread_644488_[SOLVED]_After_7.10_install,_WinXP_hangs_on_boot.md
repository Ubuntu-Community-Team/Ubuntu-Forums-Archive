---
title: "[SOLVED] After 7.10 install, WinXP hangs on boot"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by gkaufman on 2007-12-18
My System:
emachines T5026
512MB RAM
160GB HD
WinXP-Home

The HD was divided into 2 partitions - first one was 4GB, containing the system recovery from emachines, and the  rest was XP. It took me awhile, but i was finally able to get the XP partition  defragged enough for ubuntu to install. however, i still had 2 unmovable files  way out to the right side - the paging file, but couldn't get them to move to  the beginning of the drive for anything - I even used dirms as others suggested  here. I removed the 4GB partition (using the ubuntu Live CD), and as part of the install process, used gparted to shrink  the ~160GB XP partition to ~100GB, and move it to the beginning of the drive. That took about 5 hours. I then  was able to proceed with the ubuntu 7.10 install w/o incident. I rebooted and started up WinXP to make sure that was  still working, and that's where I ran into problems. I actually get pretty far in the boot process - past the XP blue "progress" bar  all the way to the blue background (not BSOD) with windows logo, right before the list of users. It then hangs there. HD spins down,  seems to be totally stuck. I've left it like that for over 2 hours with nothing happening. Hitting esc causes a beep, as does any  keypress. I have to power off and reboot. I can get to the WinXP advanced boot options (via F8), but no matter which option I choose,  they all get stuck at the same point, including safe mode, debugging, etc.

In ubuntu, I get an error about "not a clean shutdown" (or similar) when I try to mount the windows drive. I'm able to force it to be  mounted, and can then access it just fine. 

Does anybody have any ideas on what I can do to get XP to boot normally now? I really need to use a dual-boot for at least a few more  months (until I finish converting all of my .ASP files into .PHP).

any help at all would be greatly appreciated!

TIA!

---

### Post by heatpumpcontrol on 2007-12-18
I just worked on a pc that had the same issue but it didn't have Ubuntu installed. This is a microsoft security update issue that they are aware of. I don't remember the title but look it up in their database.  I will search for it and try to get back to you. It is not an Ubuntu install issue.

---

### Post by heatpumpcontrol on 2007-12-18
I did have an error msg though, do you have one?

---

### Post by gkaufman on 2007-12-18
not anywhere obvious - it just sits there

---

### Post by logos34 on 2007-12-18
> **gkaufman said:**
> ...used gparted to shrink  the ~160GB XP partition to ~100GB, and move it to the beginning of the drive. That took about 5 hours. I then  was able to proceed with the ubuntu 7.10 install w/o incident. I rebooted and started up WinXP to make sure that was  still working, and that's where I ran into problems.

Normally the first boot into windows after resizing triggers checkdisk (a pale blue screen with white lettering interrupts the windows boot right after the splash or blue welcome screen).  But it doesn't look like it ran.  Try to run it from the console -- type **chkdisk /r ** at the prompt.  Or in ubuntu run:
[B]
sudo apt-get install ntfsprogs[/B]

**sudo ntfsfix /dev/hda1** (or sda1)

it will flag the ntfs partition as 'dirty' and schedule chkdsk to run next windows boot

---

### Post by gkaufman on 2007-12-19
you're right - I did get that chkdsk message. i'd forgotten about that. i let it run, but don't remember if there was any errors after that - i don't think so, though.

i can't get to a console to run chkdisk /r

grrr.... i'm getting an error installing ntfsprogs - no installation candidate. this is not looking to be my day!

---

### Post by logos34 on 2007-12-19
nake sure you have all the repos enabled in software sources/synaptic.  It's in 'Main'

This is what were looking for (I'm running x64 -- hence the 'am64'):
> $ apt-cache show ntfsprogs
Package: ntfsprogs
Priority: optional
Section: otherosfs
Installed-Size: 704
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: David Martínez Moreno <ender@debian.org>
Architecture: amd64
Source: linux-ntfs
Version: 1.13.1-6
Depends: libc6 (>= 2.5-0ubuntu1), libfuse2 (>= 2.6), libntfs9 (>= 1.13.1), fuse-utils (>> 2.5.0)
Filename: pool/main/l/linux-ntfs/ntfsprogs_1.13.1-6_amd64.deb
Size: 274994
MD5sum: 878a860aee93a1e7d2cf95b70906ed71
SHA1: 569a8de351b37bd2cb4f7dc1088a44d7f1dd44cc
SHA256: 3b2006e5adcc95b67001a4beaba752d5dd2e6374ee3258f4187a90ec6e4f68fc
Description: tools for doing neat things in NTFS partitions from Linux
 The Linux-NTFS project ([http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)) aims to bring full
 support for the NTFS filesystem to the Linux operating system.
 .
 This is a set of tools targeted for people interested in working
 with the NTFS support in the Linux kernel and using it. The
 following utilities are included:
 .
 ntfsfix - Fix common filesystem errors and force Windows to check NTFS.
 .
 mkntfs - Format a partition with an NTFS filesystem, optionally bootable.
 .
 ntfsinfo - Show some information about an NTFS partition or one of
 the files or directories within it.
 .
 ntfslabel - Show, or set, an NTFS partition's volume label.
 .
 ntfsresize - Resize an NTFS partition without losing data.
 .
 ntfsundelete - Recover deleted files from an NTFS partition.
 .
 ntfscluster - Locate the owner of any given sector or cluster on an NTFS
 partition.
 .
 ntfscat - Concatenate files and print them on the standard output
 (without mounting the partition).
 .
 ntfsls - List directory contents on an NTFS filesystem (without
 mounting).
 .
 ntfscp - Overwrite files on an NTFS partition.
 .
 ntfsclone - Efficiently clone an NTFS filesystem or a part of it.
 .
 ntfsmount - Mount an NTFS partition from user-space using libntfs and FUSE.
 .
 ntfsdecrypt - Decrypt NTFS encrypted files.
 .
 ntfscmp - Compare two NTFS volumes and tell the differences.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-live, kubuntu-live, edubuntu-live, xubuntu-live, gobuntu-live


---

### Post by logos34 on 2007-12-19
> **gkaufman said:**
> you're right - I did get that chkdsk message. i'd forgotten about that. i let it run, but don't remember if there was any errors after that - i don't think so, though.


It sometimes can't repair all the errors.  It usually lets you know, though.  If it already ran, I'm not sure it's going to help to schedule another through ubuntu, but I guess it can't hurt to try.

---

### Post by gkaufman on 2007-12-19
thanks for the tip on the repos - I was able to install ntfsprogs, and ntfsfix ran as expected. I'm rebooting now to try windows. i'll check in here again in a few!

---

### Post by gkaufman on 2007-12-19
I'm back now - I got the chkdsk message again, but I'm afraid it didn't do any good - still hanging at the same spot.

---

### Post by logos34 on 2007-12-19
If you can access windows partition in ubuntu, at least that's something...Maybe time to back up windows files and start thinking about a reinstall.  Do you have an XP install cd? --oh wait, the recovery partition, it's gone and with it any chance to restore/reinstall xp...right?

---

### Post by gkaufman on 2007-12-19
Yeah, I was thinking that a re-install was going to be near. I have an install CD available, but dread the thought of reloading all the apps I need. I have good backups of my data, so I'm only going to be out my time. ... sigh...

---

### Post by logos34 on 2007-12-19
yeah, reinstalling win and all those apps is a real drag...takes me forever with all the reboots required.  But just for future reference you might consider making a separate data partition in addition to the C: system drive...You can put not only My Docs there but also any apps that don't need to install into the registry. Saves some time at least...

---

### Post by gkaufman on 2007-12-23
Luckily I had just made a backup image using DriveImageXML (win prog) before I attempted the ubuntu install. Eventually I was able to re-load it, but in the process I had to use my system restore disks to wipe the drive clean (and lose my ubuntu installation). After a lot of effort (and many reboots), with the use of the System Rescue CD I was able to get my image reloaded. I then started the ubuntu installation again. This time, though, I did not move the windows partition - I just resized it. I verified that I was able to reload windows before I went any further. WIth that success, I then manually created the partitions that I would need for ubuntu, and installed without further incident. 

So here I am now, finally successfully running a dual boot! WOO HOO! :guitar:

Thanks, everyone for your ideas and suggestions!

---

