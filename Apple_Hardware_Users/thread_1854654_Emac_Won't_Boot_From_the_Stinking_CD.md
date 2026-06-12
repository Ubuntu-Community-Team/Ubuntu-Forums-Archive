---
title: "Emac Won't Boot From the Stinking CD"
date: 2011-10-04
forum: Apple Hardware Users
---

### Post by Ms. Daisy on 2011-10-04
HOLY CRAP this Emac absolutely refuses to boot from the shiny, new Ubuntu installation CD I created especially for it.  I checked the specs against the system requirements and this old Emac is a perfect candidate to live life as an Ubuntu machine. No partitioning this bad boy.  I want to wipe out the Mac OS.

It won't boot from CD when upon startup I:
Hold down the "c" key
Hold down the command, option, shift and delete keys

Apparently Apple has this Open Firmware password thing that can prevent anyone from booting from a CD.  And apparently it's a triple secret how to disable said password.  After a stupid amount of time, I found a helpful soul out there that said to do the following upon startup:

1. zap the PRAM by holding down command, option, "p" and "r" 
2. physically change the RAM chips in the computer & restart.
3. clear the NVRAM by holding down command, option, "n" and "v"
4. hold down the power button until you get to the command line.  type "reset-nvram", press return, then type in "reset-all" and press return.  Then it reboots.

So I did every single one of these things, and the blessed machine still insists that it startup from the hard drive.  Does anyone have any clue how I can convince it that it is in fact destined to be an Ubuntu machine?

If not, does anyone want to come over and take a whack at my Emac pinata?  Or maybe it would be fun to have an Emac tossing party.  I wonder what would happen if I hurl it off the roof...

---

### Post by hansdown on 2011-10-04
Hi, Ms. Daisy.

Command-Option-Shift-Delete : Forces your Mac to startup from its internal CD-ROM.

I'll ask, that your post be moved to the apple section, where more help is available.

---

### Post by sffvba[e0rt on 2011-10-04
*Thread moved to **Apple Users**.*


404

---

### Post by Ms. Daisy on 2011-10-04
Thanks for moving it, I didn't know there WAS an apple forum.

Yup, I tried the command, option, shift, delete.  The emac completely ignored me and booted from the hard drive.  

I forget which of the numerous things I listed got me to a place that showed all the boot possibilities.  The hard drive was the only thing shown.  I know the CD drive works- I burned the Ubuntu bootable cd on it.

---

### Post by rsavage on 2011-10-05
Hi, did you burn the powerpc version of ubuntu?  CDs are available here [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads), but have a look at the last few pages of the powerpc sticky thread (top of the apple section) to find out how to install newer versions of ubuntu.

---

### Post by Ms. Daisy on 2011-10-05
Oooooooooh.  My ignorance about Macs demonstrates my unwillingness to learn about them.  So Ubuntu 10.10 is the most recent long-term supported version available for an Emac?

---

### Post by rsavage on 2011-10-05
Yeah, I did exactly the same thing!

10.04 is the long term version ('til April 2013).  10.10 is only supported for another 6ish months so I don't think there is much point in installing that.

If you want a later version (with Firefox 7 etc) then I would install xubuntu like I suggest on the powerpc sticky.

---

### Post by Ms. Daisy on 2011-10-08
Discovered my problem: for some reason, the download was corrupted. When I tried to "validate" the CD, it told me that the data needed repair.  I downloaded it a second time and all went well, or at least the CD passed the verification.

---

### Post by Ms. Daisy on 2011-10-08
I think that it would probably make sense for me to install Xubuntu or Lubuntu on this Emac, but the long instructions totally intimidate me.  I've started learning how bash works, but it's only been 2 weeks.

---

