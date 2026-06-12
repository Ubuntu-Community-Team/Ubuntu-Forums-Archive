---
title: "partition"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by crawall on 2008-01-06
how can i make a partition, after i installed ubuntu on my dell latitude, to put my data:confused:

---

### Post by rcsarver on 2008-01-06
dang, its pretty easy to do during the installation process by going to manual partition.

there are several applications to partition, maybe try 'partman'?

---

### Post by cartisdm on 2008-01-06
Use the Ubuntu liveCD to get gparted.

Check out this thread [http://ubuntuforums.org/showthread.php?t=602220]("http://ubuntuforums.org/showthread.php?t=602220")

---

### Post by thelatinist on 2008-01-06
Boot from the LiveCD and run System > Administration > Partition Editor.  Resize a partition with free space and create a new one in the empty space you create.  Voila!

---

### Post by PeterJS on 2008-01-06
Assuming that your existing partitions take up all the available space on the disk, you'll need to boot to a liveCD, the ubuntu installer works for this, and use Gparted to shrink one or more of your existing partitions. For the sake of making things easier you probably want to move the existing partitions as far forward as you can, this has two benefits, it pools all the free space at the end of the disk, and shouldn't change the numbering/naming of existing partitions such that you'd have to edit your bootloader setup.

---

### Post by crawall on 2008-01-06
THANK YOU,
for the fast responses and yes it was as easy as you all said

thanks again

---

### Post by cartisdm on 2008-01-06
Anytime, go ahead and mark this thread as solved unless you have any more questions:)

---

