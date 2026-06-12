---
title: "Fixing HFS+ B-tree error"
date: 2008-09-06
forum: Apple Hardware Users
---

### Post by aydun on 2008-09-06
I'm trying to fix an "Invalid B-tree node size" problem on a PPC Mac Mini.

The Mac's Disk Utility Repair does not fix the problem.

I've tried running from a live cd (edubuntu version of 6.06 LTS) and following the instructions at [http://ubuntuforums.org/showthread.php?t=314743](http://ubuntuforums.org/showthread.php?t=314743) to install fsck.hfsplus.  

From the usage info:  "r = rebuild catalog btree" which I hoped would fix my problem, but:

```
root@ubuntu:~# /sbin/fsck.hfsplus -r /dev/hda3
** /dev/hda3
** Checking HFS Plus volume.
   Invalid B-tree node size
(4, 0)
** Volume check failed.
```

Adding debug gives:
```
root@ubuntu:~# /sbin/fsck.hfsplus -rd /dev/hda3
** /dev/hda3
	Block 2 is not an MDB or Volume Header 
	CheckForClean - could not get VHB/MDB at block 156039268 
** Checking HFS Plus volume.
   Invalid B-tree node size
(4, 0)
** Volume check failed.
volume check failed with error 7 
	volume type is pure HFS+ 
	primary MDB is at block 0 0x00 
	alternate MDB is at block 0 0x00 
	primary VHB is at block 2 0x02 
	alternate VHB is at block 156039268 0x94cf864 
	sector size = 512 0x200 
	VolumeObject flags = 0x05 
	total sectors for volume = 156039270 0x94cf866 
	total sectors for embedded volume = 0 0x00 


```

Any suggestions?

---

### Post by Denis Clijsters on 2009-05-19
same problem here...

---

### Post by utgodmode on 2009-07-12
same issue with me too but couldn't fix it

---

