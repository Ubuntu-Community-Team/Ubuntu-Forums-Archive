---
title: "OSX on Internal HD; Ubuntu on External (Firewire) HD"
date: 2007-01-30
forum: Apple PPC Users
---

### Post by YoCraig on 2007-01-30
Can it be done? I see lots of info on installing both OS's on the internal and using yaboot (I think) to choose which OS at bootup. I want osx to stay where it is on my internal HD and install Ubuntu on an empty external HD I have. I would prefer to partion this drive so that it would have an Ubuntu partition and a generic partition to be shared by OS X and Ubuntu.

My bright idea for accomplishing this was to:

1. install OSX on external HD
2. boot from external HD
3. reboot from LiveCD
4. repartition external hd into 3: OSX, Ubuntu and plain 

This is where I ran into problems. the Gnome partitioner wouldn't let me partition into 3 only two and it was only a small boot partition and then an Ubuntu partition. That would be ok, though not preferred, but how could I choose to boot to Ubuntu without OSX installed to that disk?

---

### Post by linear on 2007-01-30
Yes, it can be done. Partition first, then install. Make partitions using Disk Utility, leave the first as free space for Ubuntu and format the second for OS X. 

Then let the installer automatically re-partition the free space.

You'll need to install Edgy for this to work properly, and you may also need to customize yaboot.conf to get the booting behavior you want.

---

