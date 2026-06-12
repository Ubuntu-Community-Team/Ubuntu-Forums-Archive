---
title: "Ubuntu Server edition iso"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Lilla on 2007-06-27
hi.

I have a problem installing Ubuntu server edition.  I have downloaded the iso and burn it to the blank cd. Now when I try to install a new OS I don't see the installation window. What was I doing wrong? :( maybe there is something I've missed out when burnt the cd?

---

### Post by Lilla on 2007-06-27
:-|

---

### Post by Cresho on 2007-06-27
go into pc bios and tell it to boot off cd.

---

### Post by Lilla on 2007-06-27
I did it, but it still doesn't work :( 

is burning image to the CD enough to make the CD work like  a normal bootable CD with an OS on it? I have to admit I never burnt any image to the CD before.. so I'm not really sure if that's enough :oops:

---

### Post by rahrendt on 2007-06-27
Open the disk in windows explorer if you see any iso files then you just saved the iso to disk, you need to burn as an image. You probably already did that, also try md5 or cecksum to verify the disc.

---

### Post by Lilla on 2007-06-27
> **rahrendt said:**
> Open the disk in windows explorer if you see any iso files then you just saved the iso to disk, you need to burn as an image. You probably already did that, also try md5 or cecksum to verify the disc.
no, there are no iso files.. well, I'll try to burn at lower speed maybe it will help :(

---

### Post by Golyadkin on 2007-06-27
I remember in Nero there used to be a checkbox for making a CD bootable... but the ISO itself should take care of that I guess. Maybe it makes a difference if you burn track-at-once or disc-at-once?

---

### Post by Alterax on 2007-06-27
You may have burned the ISO file to a CD.  Check this by putting in the CD and browsing it while Windows is open.  If it's just the file, bingo!  That's the problem.  Here's why, and what to do about it:

ISO is a filesystem of its own, conveniently packaged as one file.  You don't want the file on the CD, you want to make a CD with the filesystem that the ISO file represents.  To make a CD out of this, go into the Nero menu and look for something called "Burn Image to Disc".  Then you'll have to change the "files of type" dropdown to "All files".  Pick your ISO that way, burn to disc, and you should be good to go.

--Alterax

---

### Post by swoll1980 on 2007-06-27
Make sure your burning a data cd not a music one. I don't know what kind of software your using, but alot of burners won't burn data cds

---

