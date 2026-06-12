---
title: "Installed Ubuntu - Cannot Create Partition"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by sibot on 2007-05-31
Hey all,
i just installed ubuntu, i left around 50 gb of unformatted space, during installation. When i tried to go back to GPart in system-->Administration, its not there? Where can i find it? 
thanks

---

### Post by johnnyboy on 2007-05-31
Personally, i never had any luck using the available partition editor that comes preinstalled on Ubuntu.  I have repartitioned my hard drive more than once.

I downloaded the gparted livecd, copied the ISO to a cd, and then booted off of that.  This has worked for me every time.  

The ISO can be found various places, I'd suggest sourceforge.net or a regular google search.

---

### Post by aeiah on 2007-05-31
bizarrely, gparted isnt installed by default. you can get it via synaptic though, but you need to unmount the partitions you want to edit and it can get a bit messy.

like the poster above, im also a fan of the gparted livecd. its only about 50mb so it boots fast, and it uses a newer version of gparted than the feisty livecd and seems to have better support for fixing glitchy filesystems

---

### Post by GabrielDunn on 2007-05-31
Booting and formatting with G-parted is the simpliest solution.  Format the 50 gigs as ext3 and like 2 gis for a swap, set the mount point and blammo!  Boot from your linux live disk and install.

---

