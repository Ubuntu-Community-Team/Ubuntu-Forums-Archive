---
title: "Live DVD?"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by napsilan on 2006-02-02
Is it possible to get the live version to boot if you write the CD image to a DVD?  I don't have any CDRs at the moment.  I tried booting from a DVD with the cd image, and everything when fine until the "load installer components" portion.  It could not read from the cd/dvd for that.  It was obviously able to read from the dvd if it got that far, but is there something in the drivers that eventually get loaded that will only read from a cd?  

So, do i need to go and find a cdr to burn it on, or did i get a bad burn on the dvd?  Also, is it possible to get live CD's from the shipit site or are those install CD's only?

---

### Post by jasay on 2006-02-03
I have no idea why your dvd isn't working.  I don't see why it wouldn't, though I admit I've never tried.  In fact I think there is a [dvd image]("http://torrent.ubuntu.com/releases/breezy/release/dvd/") you can download that's supposed to work as both a live and install disc.  Did you check the md5sum of the iso you downloaded against the one listed on the website?  Burning at too high a speed can create errors on the disc.  

I do know that shipit sends both a live and install cd for every order.  So if you ask for 5 cd's they actually give you 5 pairs.

---

### Post by napsilan on 2006-02-06
Following up here incase anyone else has the same problem.  I did a bunch of searching around the forum and found that the problem was my benq 1640.  I had to update the firmware from bsmb to bsob.  Plextor 740a supposedly has the same problem.  

Although now for some reason when i boot the live cd, once the desktop starts to load, the ubuntu logo shows up all distorted and nothing happens from then on.  The mouse was working at that point but there was just the brown background and a messed up logo in the middle of the screen.

---

