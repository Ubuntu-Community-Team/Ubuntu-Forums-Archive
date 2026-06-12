---
title: "Accessing the hard drive with a liveCD?"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by pilotcp on 2005-06-29
Hello all, i was just wondering if it was possible to access the computer's hard drive while using the LiveCD. 


Thanks!
Charlie

---

### Post by sonny on 2005-06-29
Yes you can do that.

But you have to mount the HD, the way you do it depends on what filesystem the HD has.

First you have to find out what your HD name is, like hda1 (for the first partition of your first HD), if you have many HD or many partitions, you should install Qtparted and then check the name of the partitions, locate the one you want to mount and that'll be all, to the next step.

Once you lacate the partition you have to make mounting points for each of them, I recomend you to use the /media folder, cuz it'll show you your harddrives in the "Computer" thing. Type in a terminal:
sudo mkdir /media/hda1 (if your drive name is hda1)
sudo mkdir /media/hdb1 (for the first partition of your second drive)

Did you get the idea?

Ok. Now to the mounting proces:

For windows ntfs partition (all this code is in a terminal):
sudo mount -t ntfs /dev/hda1 /media/hda1
You can't write to a ntfs partition, it a read-only filesystem for Linux.

For Linux partition:
sudo mount /dev/hda1 /media/hda1
sudo chmod 775 -R /media/hda1 (if you want write permissions)

For a windows fat32 partition:
sudo mount -t vfat /dev/hda1 /media/hda1
sudo chmod 775 -R /media/hda1 (for write permissions)

That should be all, and you'll be able to get into the partition through the "computer" logo in the places menu.

you can type man mount or mount --help in a termial to find out more about mounting hardrives or any device.

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=pilotcp]Hello all, i was just wondering if it was possible to access the computer's hard drive while using the LiveCD. 


Thanks!
Charlie[/QUOTE]

To read to it, not write to it (if you have ntfs filesystem).

---

