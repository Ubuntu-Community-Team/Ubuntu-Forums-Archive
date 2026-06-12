---
title: "Replace UUID number with /media/hda#"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-04-10
Hi,

Pretty much fiddling with my system, wanting to understand how it works, and simplifying stuff if I can. Been studying my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=c2c73588-f179-411b-affc-4665154824e6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=D8284E00284DDE5E /media/NTFS_Programs     ntfs3g    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc1
#UUID=3CE83D23E83CDD38 /media/hdc1     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6  /media/content    ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=a3cd5a1e-aa6b-4890-9ae4-9d8121a09331 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc1  /media/x-plane    ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdc3  /media/NFS_deskdocs  ext3    defaults,errors=remount-ro 0       1
/dev/hdc5  /media/NTFS_Poser    ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdc6  /media/NFS_XPlane  ext3    defaults,errors=remount-ro 0       1

```

...and I find the mixture of direct references to media and the UUID reference mix a bit disturbing, particularly when the entry:
```
# /dev/hda1
UUID=D8284E00284DDE5E /media/NTFS_Programs     ntfs3g    defaults,nls=utf8,umask=007,gid=46 0       1

```

seems to create a problem here:
[IMG]http://www.tightbytes.com/images/ubuntu/ntfsProb1.jpg[/IMG]

whilst the /media/<volume reference> like:

```
/dev/hdc5  /media/NTFS_Poser    ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
```

creates this:

[IMG]http://www.tightbytes.com/images/ubuntu/ntfsProb2.jpg[/IMG]

Oh, and BTW, NTFS_Programs does exist in /media:

[IMG]http://www.tightbytes.com/images/ubuntu/ntfsProb3.jpg[/IMG]

My question: is it safe to take out those UUID thingies? and will it make fstab more stable or easier for Ubuntu to read, or will mucking around with it totally bugger it up?
Cheers!

---

### Post by bernied on 2007-04-10
My understanding is that the UUID is the new way, I think it means that if you swap your disks around they will still be found, so even if the disk order changes the UUID will stay the same.

But it will all still work the old fashioned way, I changed all mine back to /dev/hd_ because the UUIDs do my head in.

That thing with gparted is nothing to be worried about, I'll bet gparted still works fine, it's using the fstab file to find out where partitions should be mounted, but not understanding the UUIDs. I imagine gparted will catch up soon enough.

---

### Post by bernied on 2007-04-10
But I wonder whether the UUID stays the same if you resize or move the partition?

---

### Post by bernied on 2007-04-10
The lines like:
```
# /dev/hda1
```are just comments, BTW. If you want to change it to the old-fashioned way, remove the #, then remove the line-break and the UUID=blahblahblah.

Of course take a backup of the original before you change anything.

Test with 
```
mount -a
```
Then check whether anything has changed.

---

### Post by AtrejuT on 2007-04-10
I know the UUID of my windows partition changed when I formatted and reinstalled it, so I very much doubt it will stay the same if you resize/move it...

atreju

---

### Post by bernied on 2007-04-10
It looks like the UUID refers to a filesystem, not a device, so it's not surprising that reformatting changed it. See 'man fstab'.

A quick google shows this is a contentious issue - maybe it is good for removable devices, and for systems where disks get swapped in and out a lot, but otherwise not seen as very user-friendly.

---

### Post by chakkaradeep on 2007-04-10
> **bernied said:**
> My understanding is that the UUID is the new way, I think it means that if you swap your disks around they will still be found, so even if the disk order changes the UUID will stay the same.


How to find the UUID of a partition? Is there any command available ?

---

### Post by bernied on 2007-04-10
Here's one way, but I'm sure there's a better:
```
sudo dumpe2fs /dev/xdyz | grep UUID
```

EDIT: I think this only works for ext2 and ext3 filesystems.

---

### Post by chakkaradeep on 2007-04-10
> **bernied said:**
>  I think this only works for ext2 and ext3 filesystems.

Yes :( , anybody know for other file systems ?

---

### Post by bernied on 2007-04-10
Try this:
```
sudo vol_id -u /dev/xdyz
```

---

### Post by mcduck on 2007-04-10
> **Robynsveil said:**
> 
```
# /dev/hda1
UUID=D8284E00284DDE5E /media/NTFS_Programs     ntfs3g    defaults,nls=utf8,umask=007,gid=46 0       1

```

seems to create a problem here:

You have a typo there, it's 'ntfs-3g', not 'ntfs3g'. That probably causes the error you have.

Also, you can get UUID's for your partitions by running 'ls -la /dev/disk/by-uuid'

---

### Post by chakkaradeep on 2007-04-10
> **bernied said:**
> Try this:
```
sudo vol_id -u /dev/xdyz
```

Thanks, that worked :)

---

### Post by Robynsveil on 2007-04-11
> **mcduck said:**
> You have a typo there, it's 'ntfs-3g', not 'ntfs3g'. That probably causes the error you have.

Also, you can get UUID's for your partitions by running 'ls -la /dev/disk/by-uuid'

Thanks, McDuck, I'll fix that... and thanks to all who have responded. It's those kinds of issues that have kept me from being a really good programmer ;)

---

### Post by igknighted on 2007-04-11
There are a few reasons for UUIDs.  First, they work really well with removable file systems.  If you have several flash drives or external HDs, they can always be mounted to their proper place via UUID, while the physical name of the drive (sda/sdb/etc) might change.  Also, the driver for IDE hard drives is changing in feisty.  All hard drives will use the sata naming convention of /dev/sdX#, so by using UUID's, upgrading would be possible without wrecking the fstab.

Despite these benefits, people like me who format partitions a lot (from trying new distro's) will find UUIDs a PITA, and will resort to using the drive name.  Just be careful doing this if you upgrade to feisty, as you could trash your fstab.

---

### Post by lvanderree on 2007-04-16
After using gparted to resize my partitions (shrink windows, grew ubuntu) I found out that I couldn't grew nor move my ubuntu partitiion (to the left).

So I copied (and grew) it to the left, after which I intended to remove the old, smaller partition.

But now I have two partitions /dev/sda5 and the new /dev/sda8 which both have the same uuid! even though they obviously are not the same, and don't even have the same size....

So now I wonder where this uuid is stored and how it can be changed.

---

### Post by lvanderree on 2007-04-16
Just to let you know

I found out in this thread: [http://ubuntuforums.org/showthread.php?p=2350139](http://ubuntuforums.org/showthread.php?p=2350139)

that you can change the id of your (ext) volume with tune2fs.

---

