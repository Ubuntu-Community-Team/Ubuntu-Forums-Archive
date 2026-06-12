---
title: "Copying VCD's"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by elhombreborracho on 2007-10-17
Hi can anyone help me copy or clone VCD's. I installed K3B and when I try to copy I get the error:
K3B does not copy CD's containing multiple data tracks.
thanks

---

### Post by PhilJ on 2007-10-17
try vcdimager from repositories, but its command line

philj

---

### Post by manmath on 2007-11-27
I copy the disc to the hard disk as a raw/iso (dd if=/dev/cdrom of=/tmp/image.iso) then I use vcdgear to extract the dat to mpg:

vcdgear -raw2mpg /tmp/image.iso movie.mpg


This is pretty much the method I would recommend as well, the one change I would add is that I use readcd as it handles copying from the CD medium much better than dd, IMHO.

"vcdgear -fix -cue2mpg" has been reliable in extracting a working mpg from a standard image file set.

Just tried with DD and had an issue. readcd is a good tool, I prefer cdrdao myself and this command line should get you a lovelly bin/cue to use vcdgear on:

cdrdao read-cd --device ATA:1,1,0 --driver generic-mmc-raw --read-raw image.cue

Change the device for whatever is your reader!

OR

install readvcd and then 

# readvcd 2 > mv.mpg

OR

Install vcdimager
# vcdxrip

OR

install cdfs
mount -t cdfs /dev/cdrom (or whatever your drive is) /home/movie (or whatever your destination)

---

