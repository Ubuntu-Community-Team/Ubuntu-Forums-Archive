---
title: "Dual Boot FC6 and Ubuntu 7.04"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by blackspyder on 2007-05-20
I'm having issues Installing Ubuntu onto my FC6 drive without wiping out my FC6 install. Is there a way to make Ubuntu install in the remaining free space (80GB hard Drive w/ next to nothing on it) and can I reuse my SWAP or do I have to create a new one? Also how would I go about setting up Grub. 


Note: I have 2 MBR's one on my Windows Drive and one on the Linux Drive. This is thanks to useless software named PCAngel which doesnt allow me to alter my Boot.ini file for Windows. Linux drive is the slave

---

### Post by confused57 on 2007-05-20
> **blackspyder said:**
> I'm having issues Installing Ubuntu onto my FC6 drive without wiping out my FC6 install. Is there a way to make Ubuntu install in the remaining free space (80GB hard Drive w/ next to nothing on it) and can I reuse my SWAP or do I have to create a new one? Also how would I go about setting up Grub. 


Note: I have 2 MBR's one on my Windows Drive and one on the Linux Drive. This is thanks to useless software named PCAngel which doesnt allow me to alter my Boot.ini file for Windows. Linux drive is the slave

Boot the Ubuntu live cd, open a terminal & post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

Are you using bios to boot the different hard drives?  You can use the same swap space for FC6 & Ubuntu...by free space, I assume you mean free space in a partition and not unallocated(unformatted) space.  There are several ways to set up booting multiple distros:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
see section #9 for booting multiple linux OS

Here's an excellent guide for installing with the Ubuntu live cd:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
you should be able to choose "manual" partitiong & resize your FC6 partition, etc.

---

