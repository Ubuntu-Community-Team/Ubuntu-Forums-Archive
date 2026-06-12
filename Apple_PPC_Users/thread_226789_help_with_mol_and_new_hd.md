---
title: "help with mol and new hd"
date: 2006-07-31
forum: Apple PPC Users
---

### Post by chrluc on 2006-07-31
I have a g4 ibook which had tiger on it. The hd got trashed and i have lost my install disks for tiger. I have a copy of jaguar 10.2, but as far as i can read jaguar cannot be installed on that machine. I have installed ubuntu on the ibook and besides the airport extreem and trackpad problems (i have not found a solution to) ubuntu runs great... however I MUST use photoshop due to work. i have loaded mol and it goes thru the entire setup on for 10.2 (which would not run on the ibook by itself due to some sort of block, but ran in mol. I ran sudo startmol -x --cdboot and got to the part where it asks where to install, and there was no place. reformated the drive to put ubuntu on it. so i loaded the live cd and used gparted to create a new partition. and formatted it as ext3 (which turned out to not be reconized) and tried hfs but it has a limit of i believe 2 gig and tried fat 32 and all where not reconized as a place the os x install would accept. so what am i doing wrong? i could start over but still not sure how to partition the drive and i cant install the os x first....

thanks

---

### Post by ssam on 2006-08-19
you might need to make sure that mol is using the disk/partition you want to unstall mac os x on. have a look through ```
/etc/mol/molrc.osx
```. It is quite well commented so you should be able see whats going on.

---

### Post by ubuntuben on 2006-08-27
Wouldn't you have to create an HFS+ formatted partition in order to install Mac OS X?

---

