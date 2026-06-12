---
title: "What is LVM on disk format/partition"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-11
Downloaded 6.06 just to give it a try...

When if came to the format/partition section, it asks if I want to use LVM.

What is LVM?

---

### Post by VoidedCheck on 2008-03-11
Logical Volume Manager.
[http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))
[http://en.wikipedia.org/wiki/Logical_volume](http://en.wikipedia.org/wiki/Logical_volume)
Sorry I don't know the details, so I'm just passing the links.

---

### Post by Girya on 2008-03-14
LVM stands for logical volume management. Its a method of grouping partitions or entire hard disks into logical volumes that allow the user to grow or shrink the volume as needed. Additional hard disks can be added to the volume group.

 An example of LVM is using it on a server running backuppc that backs up a home network of a mix of linux and ms computers. As the directory that holds the backup grows to fill the hd, you just install and configure a new hd and the directory will span both hard disks. 

LVM can manage up to 16tb on 32 bit systems with backuppc this could backup something like 128tb of data. (10 Terabytes: Printed collection of the U. S. Library of Congress)

[http://tldp.org/HOWTO/LVM-HOWTO/]("http://tldp.org/HOWTO/LVM-HOWTO/")
[http://backuppc.sourceforge.net/info.html]("http://backuppc.sourceforge.net/info.html")

---

### Post by BlizzofOZ on 2008-03-14
> **Girya said:**
> LVM stands for logical volume management. Its a method of grouping partitions or entire hard disks into logical volumes that allow the user to grow or shrink the volume as needed. Additional hard disks can be added to the volume group.

 An example of LVM is using it on a server running backuppc that backs up a home network of a mix of linux and ms computers. As the directory that holds the backup grows to fill the hd, you just install and configure a new hd and the directory will span both hard disks. 

LVM can manage up to 16tb on 32 bit systems with backuppc this could backup something like 128tb of data. (10 Terabytes: Printed collection of the U. S. Library of Congress)

[http://tldp.org/HOWTO/LVM-HOWTO/]("http://tldp.org/HOWTO/LVM-HOWTO/")
[http://backuppc.sourceforge.net/info.html]("http://backuppc.sourceforge.net/info.html")


Ah, now I understand!  

Can you add LVM after the fact?  Meaning, I assume this is some kind of application and seems to added/installed upon first installing the OS.  Can you install LVM after you've partitioned the drive (I only have one at the moment) and installed the OS?

---

