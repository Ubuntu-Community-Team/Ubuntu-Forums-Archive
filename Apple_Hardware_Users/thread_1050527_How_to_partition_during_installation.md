---
title: "How to partition during installation??"
date: 2009-01-25
forum: Apple Hardware Users
---

### Post by alexalexalex on 2009-01-25
I have a powerbook g4, and I would like to have dualbooot OSX and Ubuntu. when I get to step 4 of the installation I select manual and see many partitions and do not know what to do.

Also, if I bought an external Firewire disk could I install ubuntu on that?

I would resize the partition but do not have osx install disks...

cheers!

---

### Post by utnubuuser on 2009-01-26
Firewire sounds like a good plan.

---

### Post by mkvnmtr on 2009-01-26
To me the easiest way to do a dual boot installation is to use the live disk to resize your mac partition before you start the install. I theink you should defragment with another tool before you start but there is some question if that is needed. Boot the disk and go to partition editor in system/administration. Your mac partition will be the large one with hfsplus format. Make that smaller with thee editor. Leave the space yoou creat as free space. Do not format it. It should probably be at least 10GB but can be what you want it to be. Then exit the editor and begin the install. When you get to the partitioning part choos to install on the largest free space It will form the partitions you need for boot , swap and root with no input from you. That is the easiest way for some one that installing for the first time. After the install you can install Gparted in your system and you can open it to see your partitions and what the installer did.

---

