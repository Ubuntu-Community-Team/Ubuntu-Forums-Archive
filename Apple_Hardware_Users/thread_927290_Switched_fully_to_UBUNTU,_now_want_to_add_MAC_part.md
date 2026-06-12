---
title: "Switched fully to UBUNTU, now want to add MAC partition"
date: 2008-09-22
forum: Apple Hardware Users
---

### Post by anticapital on 2008-09-22
Forgive me if this has been discussed already; I couldn't find the specific help.

I installed UBUNTU on my MACBOOK second gen, formatting the entire drive to ext3 (with separate partitions for /, /home, and swap). Now I want to partition my /home to put OSX (tiger) back on my computer. I created a FAT32 partition because my Gparted won't let me create a HFS+, but my apple install cd "can't read partitions". I don't know what to do. I'm not entirely opposed to formatting everything again if it means I get the system running smoothly. Oh, my Kernal is 2.6.24-generic.

thanks
Andy Captal

---

### Post by cyberdork33 on 2008-09-22
> **anticapital said:**
> Forgive me if this has been discussed already; I couldn't find the specific help.

I installed UBUNTU on my MACBOOK second gen, formatting the entire drive to ext3 (with separate partitions for /, /home, and swap). Now I want to partition my /home to put OSX (tiger) back on my computer. I created a FAT32 partition because my Gparted won't let me create a HFS+, but my apple install cd "can't read partitions". I don't know what to do. I'm not entirely opposed to formatting everything again if it means I get the system running smoothly. Oh, my Kernal is 2.6.24-generic.

thanks
Andy Captal

I'd wipe it to make OS X happy to start with...

Create two large partitions with Disk Utility after booting the OS X install disc. The first should be HFS+ for OS X, the second can be FAT32 or whatever... this is just filling space that will be used by Ubuntu. Install OS X normally on the partition you created. After it is finished, boot the Ubuntu LiveCD, start gParted and delete the FAT32 partition you made. After that start the installer and select "install to the largest free space" when prompted.

---

### Post by anticapital on 2008-09-23
When I "wipe it", what filesystem type should I format it to? Should I leave it just erased, without any formatting?

---

### Post by cyberdork33 on 2008-09-23
> **anticapital said:**
> When I "wipe it", what filesystem type should I format it to? Should I leave it just erased, without any formatting?
The OS X partition has a few options (just look in DiskUtility... You will probably want journaled, case-insensitive), for the partition that leaves space for Ubuntu, you can just make it FAT32 or "free" if that option is available. It really doesn't matter because you are going to delete it.

---

### Post by anticapital on 2008-09-24
thank you thank you. everything is working now.

---

