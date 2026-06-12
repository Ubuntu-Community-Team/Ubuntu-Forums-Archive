---
title: "Ig'nert Newbie - making an installer disk for ppc"
date: 2007-01-28
forum: Apple PPC Users
---

### Post by gurnemanz on 2007-01-28
I think I've got a fundamental mistake going here. See if you can identify it, please.

When I try to make an installation disk, do I copy the white 'Installer' icon to the cd or do I copy the individual elements inside the installer?

Can't seem to get my disks to boot. I hold down C, the cd drive cycles briefly, and OS X comes up.

Apple installer disks function correctly when holding down C.

Using Taiyo Uden cd blanks, Pioneer internal superdrive on a Pismo P-book, burning at 2x with Toast Light.

Signed,

Puzzled in Long Beach

---

### Post by linear on 2007-01-28
Don't copy anything. You need to burn the iso as an image to the CD. Can't say exactly how to do that in Toast Light. In Disk Utility, you would drag the iso to the left pane, then select it and use Images > Burn.

---

### Post by gurnemanz on 2007-01-28
> **linear said:**
> <SNIP> . . . select it and use Images > Burn.

Thanks! Now,  let's see if I can hold the burn speed down low enough using Disk Utility!

---

### Post by nhylo on 2007-01-28
you will be able to go down to speed 8
once you download the iso it will open in your desk top and also in disk utility provided you have tiger then insert the empty disc go bac to Disk Uttilitys  choose the iso and the click on burn that all

---

### Post by gurnemanz on 2007-01-28
Thank you - but, nope - failed again.

Does the name of the cd need to be <<xubuntu.iso>>? Mine seems to have named itselfXubuntu_PowerPC_edgy . . . or I may have farkled it up all on my own.

Feeling very, very dim . . .

---

### Post by 3rdalbum on 2007-01-29
If the name of the CD ends off being Xubuntu_PowerPC_edgy, then you've burnt it correctly.

When you say "the individual files inside the installer", does that mean that you've double-clicked on the ISO file and mounted it before you burnt it? From what I hear, that can cause the ISO file to become unbootable.

Otherwise, try CD-Rs that are designed "For Music".

---

### Post by samden on 2007-01-31
Simple instructions:

Download the .iso file.

DO NOT DOUBLE-CLICK ON THIS FILE TO OPEN OR MOUNT IT!

Open a disk burning program - disk utility or disk copy on Mac OS probably. If you are burning from a Windows computer, note that Win XP is not natively able to burn .iso files, you will need a disk burning app like Nero. If you do not have a piece of software that can burn .iso files you should be able do download an open source one, but if you have Mac OSX just use disk utility, it works fine.

Use this software to create a cd directly from the .iso file. In OSX this means select the .iso file from within disk utility, and click "burn".

You WILL NOT choose the name for the cd yourself or copy any files across. The .iso file is an image of the entire disk, including its name. If you are being asked what name to call the disk you are probably doing something wrong.

If you do not understand what .iso files are, do a forum search / Google search and read up on what other people have written about them. Opening .iso files and copying the contents to a cd is a common mistake, well documented elsewhere.

I hope this helps!

---

### Post by gurnemanz on 2007-02-01
This is really starting to tick me off. I blame the vast M$ conspiracy, of course! :lolflag: 

Using the WinTel box at work, I downloaded Xubuntu 6.10 Alternate. I made sure to see the file was suffixed with '.iso.' I burned it using Nero, selecting 'Burn Disk Image,' and burned at 4X speed.

The disk came out named 'Xubuntu_PowerPC_edgy. No '.iso' extension appended, and so no start-up from disk with 'C' held down on re-start.

I would have thought this would be the easy part of this operation!

g.

---

### Post by 3rdalbum on 2007-02-03
Well, that should work - does the drive sound like it's having trouble reading the disc? Maybe try burning to a disc that claims to be "made for music".

---

