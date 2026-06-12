---
title: "Partition"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by dogman on 2007-11-03
My hard drive has 3 partitions on.I have chosen to download to one of these partitions.Will I have to split this partition further to install and run UBUNTU?:)

---

### Post by ByteJuggler on 2007-11-03
Are you saying that the download partition currently contains only the downloaded Ubuntu CD image?  And are you saying you'd like to install to the partition that the CD image currently resides on?

---

### Post by Sef on 2007-11-03
What are you using the partitions for?

---

### Post by dogman on 2007-12-28
More detail (see also thread on installation)
I was trying to download the Ubuntu programme but it failed so ordered CD version.
Primary drive C: has windows on H,I,J are for use as storage and possible installation of Ubuntu

---

### Post by hyper_ch on 2007-12-28
Well, ubuntu doesn't use drive letters like windows. In Ubuntu everything starts from the root directory ("/").

and for Ubuntu you will need at least two partitions. 1 for the actual install and 1 for swap. The Swap partition would normally be about twice your ram up to 1 GB. Probably the simplest way is to delete one of your existing partitons. Just leave that unpartitioned.

Upon installation select then "Use largest empty space" or something like that. Be carefull in that step. Chosing the wrong one could delete all your partitions. 

If you run the DesktopCD and install from there, you'll probably also have inet access. So once you get to the partitioning, you can come here and ask again, just to be sure.

---

### Post by Sef on 2007-12-28
> More detail (see also thread on installation)

Applications > Accessories > Terminal

then type ```
sudo fdisk -l
``` (Small L)

Paste the results here.

---

