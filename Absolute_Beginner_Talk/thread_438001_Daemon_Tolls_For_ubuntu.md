---
title: "Daemon Tolls For ubuntu?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by baysl on 2007-05-09
How do I install Deamon Tolls or similiar program in ubuntu?

---

### Post by EXCiD3 on 2007-05-09
Create a mount point for the ISO:

BASH# mkdir /mnt/iso

Now mount the ISO in the mount point with the following command:

BASH# mount myiso.iso /mnt/iso/ -t iso9660 -o ro,loop=/dev/loop0

Where myiso.iso is your ISO file.

What I haven't tried yet is omitting the ro (read only) option, so that it might be possible to make changes to the ISO before finally burning, not sure if this works (will check) but the command would probably look like this:


BASH# mount myiso.iso /mnt/iso/ -t iso9660 -o loop=/dev/loop0

Taken from: [http://www.techspot.com/vb/topic483.html](http://www.techspot.com/vb/topic483.html)

See if that works

---

