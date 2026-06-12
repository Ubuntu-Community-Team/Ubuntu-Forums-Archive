---
title: "accessing partitions from ubuntu desktop"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by secallen on 2006-07-22
Hi,

Can anyone help with this problem?

I have a laptop with 80GB partitioned into 20GB Fat32 for XP, 20GB Fat32 for files and the rest unparitioned space.

I installed ubuntu telling it to use the largest contiguous available space.

After completing, I can now see the XP and file "drives" (both fat32) but when I double-click on them to have a look, I get the message "Unable to mount the selected volume". When I click on "show more details" it says "error: device /dev/hda5 is not removable" "error: could not execute pmount".
Any idea how make these drives (or "volumes"?) avialable in ubuntu??

Thanks for any advice.

---

### Post by taurus on 2006-07-22
Did you mount the fat32 that XP is on?  Assuming that it is the first partition of your first harddrive, /dev/hda1, see if it's on the list with this output?

```

df -h

```
Otherwise, you need to mount it so open a terminal (Applications -> Accessories -> Terminal) and edit your /etc/fstab...

```

sudo gedit /etc/fstab

```
Add the following line to the end of it and save it.

```

/dev/hda1     /windows     vfat     defaults,umask=00000     0  0

```
Now, create a mount point and mount it with

```

sudo mkdir /windows
sudo mount -a

```

---

### Post by Jimmy4eyes on 2006-07-22
This kind of ties in with my question. I too have a laptop with an 80Gb hard drive running XP which I'd like to partition and have the option of booting to XP or Ubuntu

I've just been reading an article on this, with videos, regarding creating the partition using GParted, for dual booting. I want to try this but it's not clear if GParted just creates the partitions, or if it also controls the dual boot selection.

Partition Magic for Windows comes, imaginatively enough, with a companion program called Boot Magic which, on first boot, would give the choice of whatever operating systems are present. Does GParted have something like this, or how would one choose what operating system to boot to?

---

### Post by taurus on 2006-07-22
Gparted from the LiveCD can only resize your partitions.  You need to use GRUB/LILO to handle booting your Ubuntu & XP.

---

### Post by richbarna on 2006-07-22
You really should use this guide, it's by one of the regular forum users, and personally I think it is the best one available.
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

