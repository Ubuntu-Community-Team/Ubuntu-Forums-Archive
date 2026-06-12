---
title: "partitian question"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by nhioi on 2007-10-17
i've been trying the livecd for quite some time, and i'd like to go with an install.

in the event that i'd like to remove ubuntu all together, giving the entire hdd back to windows, is it possible and how would i go about doing that?

---

### Post by HokeyFry on 2007-10-17
well you would have to dual boot, but first what version of windows do you have

---

### Post by santiagoward2000 on 2007-10-17
> **nhioi said:**
> i've been trying the livecd for quite some time, and i'd like to go with an install.

in the event that i'd like to remove ubuntu all together, giving the entire hdd back to windows, is it possible and how would i go about doing that?

You can erase the Ubuntu partition, and then resize the Windows one. However, you may have some trouble with GRUB. I don't know how to remove it...

---

### Post by nhioi on 2007-10-17
i have no problem dual booting.

i have windows xp pro

---

### Post by HokeyFry on 2007-10-17
well, run through the install, and when you get to the partitioning section, select manual, make the windows partition smaller, then auto partition the free space


and also, to remove grub at a later date, you have to reinstall the windows bootloader using a recovery cd or partition.


that reminds me, do you have a recovery partition on your computer that came with it?

---

### Post by nhioi on 2007-10-17
> **HokeyFry said:**
> well, run through the install, and when you get to the partitioning section, select manual, make the windows partition smaller, then auto partition the free space


and also, to remove grub at a later date, you have to reinstall the windows bootloader using a recovery cd or partition.


that reminds me, do you have a recovery partition on your computer that came with it?

no, built the computer myself actually.

---

### Post by RudolfMDLT on 2007-10-17
I recommend you giving this a read:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

It's not the begin all and end all but it's a damn good read and will put your feet on solid ground! :)

---

### Post by bigken on 2007-10-17
so you have a windows xp cd 
no probs 
if you ever need to delete ubuntu just boot into windows delete the linux partitions in disc manager

the boot into repair console with the windows xp cd and type fixmbr enter fixboot enter exit enter hey ho you boot back into windows no grub menu

---

### Post by logos34 on 2007-10-17
here are some links with screenshots of installation steps:

[https://help.ubuntu.com/community/GraphicalInstall#head-49944d8626113375eea234aa41d06d657ae5d6bf](https://help.ubuntu.com/community/GraphicalInstall#head-49944d8626113375eea234aa41d06d657ae5d6bf)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by nhioi on 2007-10-17
thanks guys :)

---

