---
title: "Can you partition a Powerbook hard drive during install?"
date: 2009-11-04
forum: Apple Hardware Users
---

### Post by apexironman on 2009-11-04
I am attempting to install (dual-boot) 9.10 on a G4 Powerbook (OSX 10.2) without reformatting the hard drive.  I ran install from the live CD and got to the Partition section of the install.  It showed OSX with the full size of the hard drive (30G) and no free space.  Can I use the manual edit feature to change the size of it's partition?  Will it accept it?  I have installed 8.10 on a few Windows boxes and had no problems, but I have little experience with Mac.  Thanks for any help.

---

### Post by linuxopjemac on 2009-11-05
you cannot just rescale the partition of OSX. I would backup the system in OSX with carbon copy cloner, then make new partitions on your mac, put back your osx system in one of the empty partitions with carbon copy cloner, install rEFIt under OSX and then install Ubuntu.

---

### Post by linuxopjemac on 2009-11-05
partitioning:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Mac%20OSX%20and%20multi%20Linux](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Mac%20OSX%20and%20multi%20Linux)

---

### Post by ndefontenay on 2009-11-05
Read some install threads for OSX if you're on MAC. I don't think it's as straight forward. I had in mind of doing so but gave up after seeing all the workarounds required to make it work.

---

