---
title: "Triple booting protocol?"
date: 2007-09-29
forum: Apple Intel Users
---

### Post by ebeyer on 2007-09-29
I'm contemplating getting a new Macbook.

I need Windows to run one application I need for my job.  Ideally, I'd like the option of booting directly into Windows, OS X or Ubuntu.  It would be even nicer if I could share files between the three partitions easily.  Even nicer would be if I could use a virtualization tool to use the other partitions so I wouldn't be rebooting left and right.

Has anybody else done this?  Are there step-by-step instructions for doing this?  I'm a relative neophyte to Linux.

EB

---

### Post by xelapond on 2007-09-29
Hi, I just recently got my Macbook Pro triple booted, sharing data between all OSes.  i did not use a guide, as there are not that many out there(none for ubuntu) but if you wanted me to i could write one on this forum.  Let me just tell you, you must reformat the entire HD to do so, and it takes a lot of work, took me at least 15 hours.  It would probably go faster if you replicated what i did, because you would learn from my mistakes.

Also, Apple has no word on how this effects the warranty, so if you even have to send your computer in just wipe it and put OS X on it.  Then re-triple boot when you get it back, that is what i do.

There are virtualization tools, some for Windows, some for Linux, some for Mac OS.  I  have tried many, and i think the best one would be VMware Fusion for Mac OS.  It has boot camp ability(same with paralells desktop, another virtualization program for Mac OS) but i do not know if it would work with a triple boot, as i have not tried.

If people on this forum want a triple boot guide i would be more then happy to write one.

---

### Post by ivesjd on 2007-09-29
I have not gotten vmware fusion to boot my windows drive on my triple boot setup. It just gives me a grub error. Grub is installed on my linux partition so thats why. If anyone knows a way around this please let me know.

---

### Post by xelapond on 2007-09-29
Grub works fine, I am using it in my triple boot.  Are you using LILO as your boot loader?

---

