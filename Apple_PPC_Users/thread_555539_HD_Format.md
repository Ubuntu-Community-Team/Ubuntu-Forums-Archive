---
title: "HD Format"
date: 2007-09-20
forum: Apple PPC Users
---

### Post by UG4tu on 2007-09-20
I was wondering what the best format is for installing Ubuntu on a G4.  I've been using the standard Mac partition for installing it, but I keep on getting errors when loading the OS.  Any info on what format would help me would be greatly apprecuated.

---

### Post by TenPlus1 on 2007-09-20
When installing Ubuntu on your hard-drive, it's best to use ext2 or ext3 formats when creating and formatting partitions, that way your using a linux standard.

---

### Post by linear on 2007-09-20
It's easiest to start with a blank partition (unformatted) and let the installer take care of it.

---

### Post by frog_pilot on 2007-09-20
There is no support in Linux for hfs+-volumes. It is impossible to install Linux on a HFS+-Volume. If you aren't experienced with filesystems in Linux, do like

linear

said!

---

### Post by UG4tu on 2007-09-20
Thanks for the help! 
Earlier I formatted the drive through OS9's disk utilities for use with Linux.  Making the whole drive the home Linux drive, which I tried installing Ubuntu on.  I'm just wondering if there is a better utility for formatting. Or am I initializing the drive as the wrong type.
I'll reply with more specifics when I return home.
Thanks again!

---

### Post by frog_pilot on 2007-09-20
There is a much better way for formatting the drive for Linux as the disk utility in OS9. The Linux-filesystem from Mac is also not supported by ubuntu.

The native installer of ubuntu on the Ubuntu-ppc-alternate or desktop cd will do this job at best.

The only thing what you have to do is to leave some empty unformatted space on the disk. About 15 Gig will be sufficient for a first test-installation. The installer will create the necessary Volumes here for the ubuntu-instllation.

---

### Post by UG4tu on 2007-09-20
Well, I used Ubuntu-ppc-alternate cd to install the OS and it came up with this error -- Warning:  file:///cdrom/pool/main/f/fribidi/libfribidi_0_0.10.7-4builder_powerpc.deb was corrupt?  The I hit continue and more and more come up... Any ideas?

---

### Post by frog_pilot on 2007-09-22
> **UG4tu said:**
> -- Warning:  file:///cdrom/pool/main/f/fribidi/libfribidi_0_0.10.7-4builder_powerpc.deb was corrupt?

On which stage of the install-process this error occurred? Never seen something like this. May be your install-cd is corrupted

---

