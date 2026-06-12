---
title: "Dual boot with OS X"
date: 2004-12-08
forum: Apple PPC Users
---

### Post by yohan233 on 2004-12-08
Hey everyone

I was really nervous putting linux on my powerbook, its my baby (G4 1.33 Ghz Aluminum)  but it's running great now.  I'm impressed at the hardware support and i'm really happy that the ubnuntu folks have put in the effort that they have to make their distro run well on the macintosh.  I'm sure it was a lot of work for not much thanks, since the mac is relatively uncommon.  Since my airport extreme doesnt work, and i really like OS X panther a lot, i want to do a dual boot setup.  As i said, ubuntu boots and runs fine, but i havent installed OS X yet.  My partitions are set up like this:

/dev/hda1     Apple_partition_map Apple        63 @ 1         ( 31.5k)  Partition map
/dev/hda2     Apple_Bootstrap untitled  1954 @ 89709168  (977.0k)  NewWorld bootblock
/dev/hda3        Apple_Bootstrap Apple_HFS_Untitled_5  89446960 @ 262208    ( 42.7G)  NewWorld bootblock
/dev/hda4         Apple_UNIX_SVR2 untitled  26498047 @ 89711122  ( 12.6G)  Linux native
/dev/hda5         Apple_UNIX_SVR2 swap       1001071 @ 116209169 (488.8M)  Linux swap

So, /dev/hda3 is a 42.7 GB partition for Mac OS X to live on, it has the bootable flag set because i get a message in the OS X installer that i cant install on it because i cant start my computer from it... but that should be easy to fix.  /dev/hda4 is the 12 GB Ubuntu root partition, /dev/hda5 is swap for linux.  This is pretty easy, but i'm wondering about /dev/hda2... its a 1 mb partition where i think yaboot lives.  Can i just reboot with the OS X DVD in the drive and install?  I have a funny feeling that OS X will do something like what windows does when it's installed and overwrite the bootloader so it'll only go into OS X, thus leaving me unable to start linux.  Ideally, i'd like to have a simple prompt where i choose OS X or Ubuntu.  I'm well aware of how this works on x86 with linux, but never tried it on PPC before.  Any help would be greatly appreciated.

great distro.

---

### Post by dkitty on 2004-12-10
I've only ever done dual boot installs the other way around... with either Mac OS 9 or X on the HD first (at the back door of the drive). I left plenty of free space and installed linux on that.

However, your reasoning seems sound to me. I think you did the right thing with the partition map in hda1. Or did you have much choice with that?

I ran YDL, OS 9, and OS X on my iBook for a while. Occasionally I'd be in either OS X or OS 9 and wish to switch to the other Mac OS and not bother with yaboot. So I switched the boot partition in the control panel of whatever Mac OS I happed to be in at the time and booted to the other Mac OS. That partition was then the default boot partition. When and if that happened I just zapped the p-ram (Command-Option-P-R keys) on reboot.

Good luck on the dual install. Please post a bit about how it worked. I'm curious.

---

### Post by yohan233 on 2004-12-11
Here's how it went down:

I went ahead and installed OS X.  During the installer, you open up the disk utility to partition your drive.  Use a two partition scheme.  Make the first partition for Mac OS X.  Label this one "Macintosh HD," or whatever you like.   Leave the second partition like it is, HFS+ is fine for now.  Finish installing and updating OS X... takes a while.  Then boot the Ubuntu install disc.  When you get to the partitioner, delete the second partition you created in the OS X disk utility.  That partition was sort of a placeholder, if you will.  Then I just told Ubuntu to automatically partition the free space, it created the appropriate root, swap, and boot partitions.  Once the install completed i had a menu that said l for GNU/linux, x for mac os x, and c for cdrom.  Works like a charm.

---

