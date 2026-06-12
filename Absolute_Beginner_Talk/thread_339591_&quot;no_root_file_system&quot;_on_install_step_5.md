---
title: "&quot;no root file system&quot; on install step 5"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by jkrtest on 2007-01-16
Hi all,

I searched for an answer, but couldn't find anything.
I am installing Edgy on a new 200GB HDD.
The live CD works like a charm, so I want to install Ubuntu permanently.
I partioned the drive with the Gparted live CD as follows:
primary partion (/dev/hda1): 20 GB, NTFS - Windows not installed, just kept the space in case I need it.
Extended partion (/dev/hda2): 186 GB, logical partitions within:
- /dev/hda5: ext2, 100GB
- /dev/hda6: ext2, 60GB
- /dev/hda7: ext2, 6 GB
- /dev/hda8: swap, 1.32GB

So finally, here is the issue:
During the install process, I get to step 5 "Prepare mount points"
no matter what I select, I get the error "No root file system"

Like at psychocats, I call the (future) Windows partion /windows.
hda5 is called /media
hda6 is called /home
hda7 is called /
hda8 is called swap

But no matter what I call the mount points, I have found no way to get past the error.
I don't even understand the error. Aren't I in the process of installing the root file system?

Or does Ubuntu need Windows already installed in the first (primary) partion?

Help, please!

Cheers!
==k

---

### Post by bodhi.zazen on 2007-01-16
> **jkrtest said:**
> Hi all,

I searched for an answer, but couldn't find anything.
I am installing Edgy on a new 200GB HDD.
The live CD works like a charm, so I want to install Ubuntu permanently.
I partioned the drive with the Gparted live CD as follows:
primary partion (/dev/hda1): 20 GB, NTFS - Windows not installed, just kept the space in case I need it.
Extended partion (/dev/hda2): 186 GB, logical partitions within:
- /dev/hda5: ext2, 100GB
- /dev/hda6: ext2, 60GB
- /dev/hda7: ext2, 6 GB
- /dev/hda8: swap, 1.32GB

So finally, here is the issue:
During the install process, I get to step 5 "Prepare mount points"
no matter what I select, I get the error "No root file system"

Like at psychocats, I call the (future) Windows partion /windows.
hda5 is called /media
hda6 is called /home
hda7 is called /
hda8 is called swap

But no matter what I call the mount points, I have found no way to get past the error.
I don't even understand the error. Aren't I in the process of installing the root file system?

Or does Ubuntu need Windows already installed in the first (primary) partion?

Help, please!

Cheers!
==k

First I would advise ext3 rather then ext2. Ext3 is journaled which means your data is more less likely to be lost if there are problems .....

Second, Linux (Ubuntu) can be installed into any partition, primary, extended/logical so that is not the problem ....

Did you check the md5sum of the downladed CD. I would assume it is OK ....

If the desktop CD fails to install, however, you may need to go with the alternate CD. The alternate CD is text based and here is a how-to:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by NeoLithium on 2007-01-16
When you assigned the mountpoints, did you select the options to format the new partitions as well? Just wondering cause I had a few small snafu's when I set up my partitioning scheme with the install CD...

---

### Post by jkrtest on 2007-01-16
thx for the replies!
I tried this thread's suggestion and it worked:
[http://ubuntuforums.org/newreply.php?do=newreply&p=1700787](http://ubuntuforums.org/newreply.php?do=newreply&p=1700787)

I'll try the ext3 - but for now I just want to install the sucker :-)

And no, it didn't matter what reformat option I checked.

Cheers!
==k

---

### Post by NeoLithium on 2007-01-16
Well, the important thing is it's working out for ya :)

---

### Post by jkrtest on 2007-01-16
so the install dialog just told me there are "uncorrected errors" in hda5. Whatever that means in a blank partition.
So I went back to change the partions to ext3

See what that'll get me...

==k

---

