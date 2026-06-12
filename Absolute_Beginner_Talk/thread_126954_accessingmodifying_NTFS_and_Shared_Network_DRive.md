---
title: "accessing/modifying NTFS and Shared Network DRive"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by whiter on 2006-02-07
okay, my only problem with installing ubuntu is this:

is it possible to access AND modify my NTFS slave-drive? 

and then after thats sorted out, how can i make sure it is able to be accessed from a windows computer on the network? simillar to the windows drive shares.

---

### Post by goatflyer on 2006-02-07
Access ntfs, yes.  although they say modifying ntfs is a risky proposition.  I keep my ntfs partitions accessible read only.  I just use another FAT32 partition as a spare 'transfer' drive, when I can easily share files from Ubuntu with my windows half.

To allow Ubuntu to be accessed from other Windows machines you will need to install and set up samba.  Being somewhat of a newbie myself, I don't know much about it, but there are plenty here on the forum who do.

---

### Post by kingsidy on 2006-02-08
check the help section in the system menu, and click on the starter guide 5.10. it explains how to use samba to set up a share.

---

