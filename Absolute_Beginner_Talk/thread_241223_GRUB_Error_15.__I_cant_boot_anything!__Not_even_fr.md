---
title: "GRUB Error 15.  I cant boot anything!  Not even from a CD! Help!"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by andyeddy525 on 2006-08-22
here's a good one:

i dual boot XP and Ubuntu using Grub.  this evening i updated the nvidia graphics drivers in ubuntu and restarted x, which spat out a large array of errors.  i played around with it for a while and decided it was time to just reload ubuntu.  needless to say, the installation locked up, and i ended up restarting the computer (i know i know, bad idea).  after the bios loads, i get an error that looks like this:

----------------------------
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 15
----------------------------

it wont boot from a CD-ROM (linux or XP or otherwise), which is first in the boot order in system setup.  it doesnt seem like the computer should need to access the MBR to boot from a CD.  the information on the drive is not valuable.  but how can i recover the drive? its a 2.5 inch laptop drive, and i'm not sure how to set it up as a slave...

---

### Post by catlett on 2006-08-22
Grub has nothing to do with booting from a cd. What happened is you erased the ubuhntu partition when installing. Grub is on the ubuntu partition. Only a very small part of grub is on the mbr. All that tiny part does is point to to the boot folder where the rest of grub is. 
Before the install cd loads the OS on your hard drive, it formats the drive. Formatting erases all data. The error from grub is happening because the first part of grub on the mbr is looking for grub on the root partition but it can't find it.
Your solution is to run the installation again. Keep working onm the boot from a cd. It should work or at the least grub is not what is causing the cd boot issue.

---

### Post by andyeddy525 on 2006-08-22
thanks for the reply.  if i could, i would wipe everything and start a clean install.  but the problem is this: my computer wont boot from a CD, even though CDROM is first in the boot order, and is recognized by the system (it shows up when you first turn on the machine).  When I select to boot from the drive (with either the XP or Ubuntu CD in it), i get the 'GRUB Error 15' screen.  it seems this is less a problem with GRUB than it is with my computer being able to boot from a CD.  but it used to be able to.  i've installed windows and ubuntu many times from the install and live disks.  

my machine is an HP tc1100 tablet pc.
the CD drive is a USB external.
i dont have a floppy drive.

---

### Post by thedivvyman on 2006-08-22
Hi - first of all I am a complete begineer on linux so  know absolutely nothing about ubuntu apart from what I've read on these forums. However  I  have  had  a  similar  problem  to  you  when  my  sons  pc  would  not  boot  at  all. It  turned  out  to  be  a  corrupt  MBR. The fix I used was to go to the HDD  manufacturers  website  and  download a bootable file to recover and zero fill the drive. As you probably know, this completely wipes  the  drive  ready  for  a  clean  install.

Hope  this  helps

---

### Post by monroetransfer on 2007-12-10
I'm having the same problem! I can't boot from anything. PLEASE can somebody help? Isn't there a solution *somewhere?*

---

### Post by HereInOz on 2007-12-10
A couple of things that may shed some light on this.

First, get into your bios and set all boot devices to CD-ROM if you can, or disable all other boot devices.  Does it still try to boot from the HDD?

You could also try, as an experiment, to disconnect the HDD, and then attempt to boot from the CD.  If it doesn't boot, you have an issue other than the installation on the HDD.

Do you have a floppy drive?  If so, try booting from that.  If bootable, get a copy of Darik's Boot & Nuke on a floppy and nuke your HDD, then start again.

---

### Post by Sef on 2007-12-10
If your GRUB is corrupted, then download [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/") and use that to reinstall GRUB.

---

