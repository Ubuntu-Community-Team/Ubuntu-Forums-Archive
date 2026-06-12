---
title: "Re-Assigning Partition Space running Windows with Ubuntu"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by yawaradil on 2007-08-31
Folks,

i am a new comer to ubuntu i like what i c.. (wink wink). i have a dell e1405 ubuntu asked me how much space should i assign to partition the har drive.. i assigned way more than its required for ubuntu to run.. 

how can i reassign more space to windows..

thanks

Newbie

---

### Post by vanadium on 2007-08-31
You will need to resize the partitions. This can be done using the graphical partitioning utility gparted. This should be run from a live CD because your system partitions obviously may not be used. After loading the live CD, you can start gparted typing its name from the command line. You need to unmount the partitions you want to change (right-click the partition). Then you will need to resize the partition that is too big, eventually move it to the end of the disk and then resize the other partition to take the freed space.

Some people are going to recommend you to download and burn the dedicated gparted live CD for this, and they are probably right (I guess it won mount the volumes in the first place). However, it can also be done with the Ubuntu live CD.

Be sure all your user data are backed up before trying this! There is always a risk that something goes wrong during such operation, either in software or due to "human error".

---

