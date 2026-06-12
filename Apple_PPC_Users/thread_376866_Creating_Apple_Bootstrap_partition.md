---
title: "Creating Apple_Bootstrap partition"
date: 2007-03-05
forum: Apple PPC Users
---

### Post by soccerdude on 2007-03-05
so, I've been trying to install Ubuntu on my 12'' powerbook G4 by manually defining my partitions.  However, the installer cannot find a NewWorld partition.  I've spent over two hours reading articles on the net trying to find how to do that to no avail.  

the exact message is: "No NewWorld boot partition was found.  The yaboot boot loader requires an Apple_Bootstrap partition at least 819200 bytes in size, using the HFS Macintosh file system."

In addition I tried going back in the installer to allow Linux automically define those partitions for me but that option is no longer available (I'm assuming because I've already partitioned some of my drive).  Therefore it seemst that I am stuck to do the partitions manually.

Please help

---

### Post by alexforcefive on 2007-03-05
This tripped me up too when I was installing ubuntu. Go back to the partition page, then delete the partitions you've created. Then go back to the start and select "use the largest available free space" :)

---

### Post by soccerdude on 2007-03-07
thank you for the suggestion.  I deleted all my partitions and the installer did indeed let me use the automatic partitioning option.  Even though I'd still like to know how I could fix the problem with the bootstrap partition, I do have Ubuntu running, and that's good enough for me.  :mrgreen:

---

