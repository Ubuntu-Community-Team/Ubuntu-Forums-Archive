---
title: "Dapper No-Go on Clamshell iBook."
date: 2006-06-06
forum: Apple PPC Users
---

### Post by AlphaMack on 2006-06-06
So I decided to slap Ubuntu on an old 300 MHz toilet-seat iBook that was previously running OS X 10.3.9 at a speed of a banana slug...

Neither the Dapper desktop nor alternate CD will start up.  Upon the "Loading ramdisk" output, I'm dropped into Open Firmware and cannot boot into Ubuntu.  The CDs aren't bad because they boot on my PowerBook G4 just fine and in Dapper they are recognized as Ubuntu CDs.

I was about to trash my Breezy CDs that were never used as I figured that Dapper was good enough to supercede them.  I fished them out of the trash, slapped the live CD first, then the install CD...and whaddayaknow?  In no time I had Breezy running on the iBook.  Both CDs worked flawlessly.

Now, can someone tell me what the heck is up with Dapper and this iBook?  Is this machine simply too old for Dapper?

Edit:

See reply below for update.

---

### Post by Rxke on 2006-06-06
I'm a clamshell user too, and here Dapper works flawlessly, but I did an upgrade from Breezy, not a CD-install. Simply starting the update manager and following the on-screen instructions. You do need net access for that, though. 

So, Dapper works on the Clamshells, further than that I can't help you.

---

### Post by warp99 on 2006-06-06
I have Dapper working on a first generation Clamshell, but there is a slight problem. I have to run with the old kernel because of a non-boot issue with the current kernel. There is a bug fix committed on this, which should make it's way onto the CD images. :cool: 

Bugzilla Link:

[http://https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508]("http://https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508")

Edit: I'm typing this entry on the Clamshell as we speak. :cool:

---

### Post by AlphaMack on 2006-06-07
[QUOTE=warp99]I have Dapper working on a first generation Clamshell, but there is a slight problem. I have to run with the old kernel because of a non-boot issue with the current kernel. There is a bug fix committed on this, which should make it's way onto the CD images. :cool: 

Bugzilla Link:

[http://https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508]("http://https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508")

Edit: I'm typing this entry on the Clamshell as we speak. :cool:[/QUOTE]

Turns out this issue has been around for quite some time:

[QUOTE=markuspm]I see the identical problem on my clamshell ibook G3 1st revision (one usb, no firewire) .

When attempting to boot the Live CD Ubuntu 6.06 (built on 20060331), yaboot sends me into Open Firmware and an error message appears:

yaboot:
----------

boot: live
Please wait, loading kernel...
Elf32 kernel loaded...
Loading ramdisk...

Open Firmware:
---------------------

Can't allocate initial device-tree chunk
Apple Powerbook2,1 1.3f1 BootROM built on 10/28/99 at 18:10:16
Welcome to Open Firmware
 ok
0 >[/QUOTE]

[http://ubuntuforums.org/showthread.php?t=121214](http://ubuntuforums.org/showthread.php?t=121214)

This is EXACTLY the same issue I had with Dapper Final on the same hardware (original iBook).

---

