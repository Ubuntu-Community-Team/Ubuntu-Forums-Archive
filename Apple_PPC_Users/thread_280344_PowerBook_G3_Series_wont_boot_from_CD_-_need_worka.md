---
title: "PowerBook G3 Series wont boot from CD - need workaround."
date: 2006-10-19
forum: Apple PPC Users
---

### Post by paxteq on 2006-10-19
HI all

I have a rescued 1999 PowerBook G3 Series (Bronze keyboard) "Lombard" this has the default OS9 install (2 partitions)

It came with a CDrom from a Wintel lappy which will mount and view CDs in OS9 but will not work as boot media.

It would be good but not imperative to reformat one parition and dualboot OS9.

I can put an ISO onto an OS9 partition, but can I boot from it and get to the partitioner?

Or maybe network install from another machine?

is there a partioner in/for OS9 that can create ext3 or reiser?

Where do I go from here? I would hate for this beauty to become an artifact.

---

### Post by paxteq on 2006-10-31
Update

I have made a little progress...

I have copied the Ubuntu CD and the yaboot files to my 'system' folder in OS9.  I can run yaboot via the openfirmware prompt.

Yaboot warns me that "Apple_hfs" should be "Apple_bootstrap"

When I run 'hd:0 \install' it kernel panics with the error: please ammend a correct "root=" option

Where now?

---

### Post by paxteq on 2006-10-31
OK - a bit further. ](*,) 

I have found info about yaboot.conf and have edited the file.

As I am trying to install from files in the blessed directory to an empty hfs+ partition.  (i assume the installer will allow me to prepare this)

Where should i point 'root=' in this case?

---

### Post by madman91 on 2006-12-09
BUMP

I too have a powerbook g3 and I want to install ubuntu linux on it. I am not quite as familiarized with the mac as the paxteq , so noobify it please :D. Sorry for hijacking, but when I hold C on my powerbook it won't boot to my ubuntu cd.

Thanks,
Greg

---

