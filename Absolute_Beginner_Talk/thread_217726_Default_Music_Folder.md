---
title: "Default Music Folder?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by Guns90 on 2006-07-17
I am using Dapper on my hda1.  I have an hdb1 loaded with Breezy.  I have documents and music on it, but I can't find them.  I tried to mount hdb1 and consequently have a have a 'storage' folder on hda1 that was created when I followed the how-to at [http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html) , but when I access the 'storage' folder I cannot find any of the data on the Breezy hdd (hdb1).  

This is my current fstab...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1 /storage ext3 defaults 0 0

---

### Post by NESFreak on 2006-07-17
check /home/<you>/

---

### Post by aysiu on 2006-07-17
Did you do ```
sudo mount -a
``` after modifying your /etc/fstab file?

---

### Post by orb9220 on 2006-07-17
Shouldn't your line: /dev/hdb1 /storage ext3 defaults 0 0
actually be          /dev/hdb1 /storage/hdb1 ext3 defaults 0 0

Because you are telling dapper that your storage is on hda instead of where it really is hdb

---

### Post by Guns90 on 2006-07-18
Yes, aysiu, I did input the 'sudo mount -a'.  I did everything the howto directed.  I even did it a second time.  All terminal commands were done by 'copy and paste' so I know that I didn't make any mistakes.  I just can't figure out why I cannot see the hdb1 in the 'computer' window, or why the music files (and only music files) from hda1 are showing up in the 'storage' folder (which shows that I'm accessing hdb1 by the way).  I guess that I must have done something else that makes it display like this.

Bottom line, I can live without the files I had on hdb1, but how/where do I find hdb1 if it's not in places> computer so that I can refortmat it, copy to it, etc.?

---

### Post by aysiu on 2006-07-18
If it doesn't show up in Places > Computer, your partition table may be corrupted?

---

### Post by Guns90 on 2006-07-18
When I installed Dapper on to the new hda1, I did not have the hdb1 hdd connected.  I did not establish partitions; everything is by default.

---

