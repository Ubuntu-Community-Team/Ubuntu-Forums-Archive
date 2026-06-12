---
title: "What is LVM?"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by goodpasture on 2007-11-09
I am having problems installing from the live cd so i Downloaded the alternate text version hoping to get a linux box today so i can play. I am at the partition manager and one of the options is guided - use entire disk and setup LVM.

What is LVM and do I want to install it ?? or just use guided - use entire disk.

thanks,

Jonathan

---

### Post by wariola on 2007-11-09
LVM is Linux Volume Manager. In a simple term, one of the coolest features is increasing your original hard drive space on-the-fly if you put your new hard drive in. E.g. if you have an 80GB hard drive, you can add another hard drive, say a 80GB hard drive and make the OS recognize it as a 160GB hard drive. The requirement are that your old drive must be formatted using LVM. 

LVM is not a filesystem but its some kind of wrap the filesystem inside it.

LVM is also not automatically mounted but you must manually point "mount" directly to the volume.

That is as far as I knew... put it simply, imagine you want to deploy a fileserver and on 1 fine day the storage suddenly about to full. With LVM you can dynamically increase the hard drive space by mounting the new drive together with the old hard drive.

It can also do a lot more things than this. More info can be found at [http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)

To answer your question, well I suggest do not install LVM on your new desktop/notebook if you just want to use for your personal usage.

---

### Post by amingv on 2007-11-09
I think [this]("http://en.wikipedia.org/wiki/Lvm") can help you more than I can...

---

### Post by goodpasture on 2007-11-09
Thanks! That really sounds cool but I just chose use entire disk only. It is just a learner system for me. And hopefully someday a ROR development machine.

Jonathan

---

