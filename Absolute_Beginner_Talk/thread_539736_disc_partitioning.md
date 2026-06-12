---
title: "disc partitioning"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by malty on 2007-08-31
Attempting to install 7.04 from downloaded, burnt iso onto my dell dim 5000. Partitioning the hard disc has my head in a spin.
I have 2 hard drives...1/ 160gig with XP and all my stuff.
                                     2/ 500gig, recently added and with 4 partitions..
                                                      E..150gig used for full Acronis backup and now 80% full.
                                                      G.. 230gig future home for my ape collection.
                                                      H,, 46gig (empty as yet) designated as a primary.
                                                      J.. 39gig  also empty as yet.     
I tried a manual partitioning but could not understand the renaming "/" prompt bit or where to put the swap file (do you create another partition for this?
I tried auto partitioning but was scared off because it did not recognise the 4 partitions within the drive, the way windows explorer does. All it shows is my original 160gigger and the 500gig drive. When I highlight this drive the only way forward is to agree to using the entire disc and nuking any exsisting goodies on it. There does not seem to be any provision for picking individual partitions on an already partitioned disc.

---

### Post by wolfen69 on 2007-08-31
try unplugging all drives (power connectors) and leave one for ubuntu. install. it has no choice but to pick that drive. reconnect drives,(with power off!) then you can choose which drive to boot to at startup.(most bios's have a quick boot option at startup to pick which HD to boot from)

---

### Post by bodhi.zazen on 2007-08-31
> **wolfen69 said:**
> try unplugging all drives (power connectors) and leave one for ubuntu. install. it has no choice but to pick that drive. reconnect drives,(with power off!) then you can choose which drive to boot to at startup.(most bios's have a quick boot option at startup to pick which HD to boot from)

LOL

Well, my advice is to learn a little about Linux partitioning.

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

In linux / == C:\

the physical partition is /dev/xxx

---

### Post by wolfen69 on 2007-08-31
yes, it wouldnt hurt to learn how to partition. once you do that, then you WILL use my method! just kidding. sort of.

---

### Post by Stan_1936 on 2007-08-31
I had no problems with this:
[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

---

