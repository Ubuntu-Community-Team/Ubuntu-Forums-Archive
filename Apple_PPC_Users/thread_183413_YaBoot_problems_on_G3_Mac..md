---
title: "YaBoot problems on G3 Mac."
date: 2006-05-28
forum: Apple PPC Users
---

### Post by kitpierce on 2006-05-28
I loved my PC Ubuntu/Kubuntu installs thus far and have decided to branch out a bit by installing on a Mac.  I have absolutely no Mac experience, so please bear with my stupidity and/or ignorance.

I got my hands on an old Blue/White G3 (somewhere in the neighborhood of 450Mhz or so) the other day from a friend and want to install Linux on it.  I don't want to dual boot or keep an old MacOS on it, just Linux.  I tried installing Kubuntu 5.10 but couldn't get it to boot.  I tried a 5.10 Live CD and it runs with no problems.  But when I tried an install, it would go through the entire process, prompt me for a reboot, and then stop at the yaboot section.  It would keep cycling through stage 1 and stage 2, then stage 1 again, etc, etc....

I beat my head against the keyboard for days and finally tried a few other distros.  SUSE 10.1 installed and ran great, but I would really prefer Kubuntu.  So I downloaded the RC for 6.06 and it's live CD function runs GREAT, as does the install.  But when I get to the reboot to run from the hard drive, I get the same errors as with 5.10.  I am pretty sure this is a problem finding a bootable image on the drive, but cannot figure out for the life of me where to go from there.  All other info I see suggests installing the MacOS first and then tweaking the Linux install to dual boot, but again I do not have a MacOS, nor do I want to run OSX (or OS9 or OS8 or anything else.)  If anybody else out there has written or knows of a how to that would get my Mac up and running, I would REALLY appreciate it.  Thanks!

---

### Post by kitpierce on 2006-05-28
Update: Tried another install using a fresh 5.10 Installation disk.  Still no go.  I format the drive with the Apple, Boot, Root, and Swap partitions as suggested and it still cycles through the stage one and stage two of yaboot.  Anybody have any ideas?

---

### Post by EuroCity on 2006-05-29
The blue and white Power Mac G3 shouldn't have the 8 GB boot partition limitation (which the beige G3s have): so the best option would probably be to choose the automatic partitioning method, thus erasing the whole disk and letting the Ubuntu installer automatically allocate the bootstrap, root and swap partitions.

Maybe you could try that and see if it works...

---

### Post by kitpierce on 2006-06-29
Latest update: After trying the above suggestion (both with partitioning a separate /home partition and without) I was still unable to get YaBoot to work.  I finally gave up and decided to wait until 6.06LTS was released.  Earlier this week, my ShipIt CDs arrived in the mail - so the story continues.

I tried to use the CDs to install a 6.06, but since the Mac doesn't have enough memory, it kept dropping me into a terminal promt instead of loading the live CD.  So I downloaded the alternate CD, and that installation progressed as normal through the entire process.  Upon reboot, I again got the unbootable Mac folder/Question mark in the center of the screen.  On a whim I decided to use the SUSE10 installation discs, because I noticed they have an option to boot the installed system.  To my shock, using the SUSE CD as a sort of "boot-disk" worked like a charm.  I am able to then access the Ubuntu GDM and log in like normal.  The down side is, I still don't have a working YaBoot and I would like to not have to keep using a SUSE CD to boot Ubuntu - since the process takes about 5 minutes and requires much hand holding by the user.

Since SUSE boots Ubuntu, I know the installation worked and it HAS to be a problem with the boot loader.  If SUSE Yaboot works, why doesn't Ubuntu's?  I tried using Synaptic to uninstall yaboot (and anything that was installed with Yaboot in the description) and then reinstalling, but that didn't make any difference.  Is there a way to copy Yaboot from the SUSE disc to the hard drive?  If so please give *very detailed* directions and I will try that.  Or can someone point me to a working Yaboot for a blue and white G3 and give some direction as to how to install it locally?  I am ***sooooo*** close I can taste it, and would very much like to figure out what's going on.  Thanks a ton!  :confused:

---

### Post by marko on 2006-06-30
As if you really needed to hear this, but you are not alone.  I have ran through the exact scenario with no joy.  Except I have installed Breezy with success on that blue/white Mac.  Tried to apt-get dist-upgrade it to Dapper and failed at same spot.  Multiple times.

If you find an answer to this, I want to know!  =)

---

### Post by kitpierce on 2006-11-24
I finally got this to work by doing two things.  I am not entirely sure which one worked, so I will list both:  First thing I did was replace the stock video card (ATI?) with another mac card that I had.  I believe the real fix was the second thing though.  I plugged in a spare hard drive and installed the OS to that drive instead.  I believe it had to do with problems installing to the IDE hard drive; the addition of the SATA drive worked like a charm.  Hope this helps!

---

### Post by Scott Atkinson on 2006-11-24
I'm glad you got it running, but I'm not sure how either of your fixes could have solved the problem.

6.06 has so far been unbootable on a b & w g3 I acquired.

Like you, I've watched yb cycle between stages 1 and 2. There is lots of advice on how to cope with this problem, both here and on other ppc-linux sites, but no one seems to have a definitive answer.

I'm assuming open firmware isn't finding yb, but my awkward attempts to write something to steer it have failed.

Thoughts? Anyone?

Best,

Scott A.

---

### Post by Gen2ly on 2006-12-08
I have a clamshell G3 ibook, 300 mHz and uBuntu runs beautifully on it!  I tell you if you get it running it's worth it.  Unfortunatly I've had problems with yaboot as well.  At time I get hangs on boot up into Linux but worse I can't boot OS 9 at all.  I've tried a number of things but the problem lies in yaboot - it does something to the directory tree, or PRAM.  Sorry wish I could be more help.  If I find something out I'll definitely let you know here.

---

### Post by 3rdalbum on 2006-12-09
The ybin command reinstalls Yaboot; give that a go. If it doesn't help, try doing a "man yaboot" and looking for any other commands to try (sorry, I'm away from my Mac at the moment).

---

### Post by Gen2ly on 2006-12-11
yeah, 3rdalbum, I've had a bad time with this.  I've read all about yaboot (man, and html documentation).  I've reinstalled yaboot enough times to have it etched on the inside .of my skull.  I've tried to update the open-firmware, reinstalled once.  
I can use 'Drive Setup' to Update the Driver and MacOS will boot, but that does some serious wacky stuff to the partition-table, disk has to be fsck'd , and yaboot installed again.  Yaboot does have a mailing list, but it's not searchable.  I do plan to go thru it though.

---

