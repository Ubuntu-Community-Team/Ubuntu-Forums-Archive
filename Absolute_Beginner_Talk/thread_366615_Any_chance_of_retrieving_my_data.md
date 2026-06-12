---
title: "Any chance of retrieving my data?"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by squidward_tentacels on 2007-02-21
Um, where to start...
I had a 40gb drive as my primary drive setup in 6.06. I also had a small slave drive (8 gb) set to auto mount for additional storage (/media/share). Everything worked just fine untill I cloned my 40gb drive onto a larger drive. Upon replacing the primary drive back into the box, I am no longer able to mount the slave drive. 

I have fstabed until I turned blue in the face. I dont think the problem lies with fstab, but rather with the disk itself, to all apperances the partiton table has become badly corrupted...:(  Which is really unusual, as I made no changes to the slave drive.

Some of my more choice errors recieved are as follows;

```
user@localhost:~$ sudo mount -a
Password:
mount: special device /dev/hdb1 does not exist

```

Which it obviously does, as it can be seen, at its correct size (though not enabled, or browsed)
through System > Administration > Disks  GUI

```
user@localhost:~$ sudo fdisk -l

Disk /dev/hda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       20023   160834716   83  Linux

Disk /dev/hdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1            2089        6038    31717634+  83  Linux
/dev/hdb2            2089        4178    16777472    0  Empty
Partition 2 does not end on cylinder boundary.
/dev/hdb3            2089        4178    16777472    0  Empty
Partition 3 does not end on cylinder boundary.
/dev/hdb4            2089        4178    16777472    0  Empty
Partition 4 does not end on cylinder boundary.

```

I have run the testdisk util, on both normal & deep scan modes,  and it failed to find any partitons at all, If anyone has any ideas on how I might be able to mount this disk, or retrieve my data, I would be estatic:) 
Also any ideas what might have happened to my partitons? I swear I never touched the slave, I just pulled the master out, cloned it and put the new master  in, I thought surely my slave would be fine...

Any Thoughts?

---

### Post by Old Pink on 2007-02-21
Google "Gparted LiveCD" :) 

That'd be my last try.

---

