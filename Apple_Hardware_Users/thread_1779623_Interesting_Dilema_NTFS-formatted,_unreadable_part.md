---
title: "Interesting Dilema: NTFS-formatted, unreadable partition."
date: 2011-06-10
forum: Apple Hardware Users
---

### Post by bware on 2011-06-10
As it says.  My colleague needed a backup for some of his loose media, so I assured him I could back it up on our Lab's Lacie 2TB external.  His windows partition was incredibly sluggish, so he booted into ubuntu 11.04 and we partitioned and formatted an NTFS volume for him to transfer his stuff to.  The format went fine, space was available, and I left him to transfer all of his stuff from his dell studio1555.  He finished and reformatted his computer completely.

So here's the problem:  The NTFS is not recognizable by any of the OS now.  
Ubuntu sees it as a single partition without any data, whereas before the transfer, the partition map was clearly visible.  
Windows does not recognize the drive at all.  
OS X does recognize the partition, but it shows up as an apple_scratch volume, which is quite a bit frightening, considering a scratch volume is essentially blank.

To elaborate, all of the files were in his windows partition, and were transfered within a relatively fresh install of ubuntu (not much had been done on it).  The partition was made in diskutility in ubuntu (the GUI), but the rest of the drive was HFS+ formatted.

---

### Post by srs5694 on 2011-06-11
Quite a few critical details are unclear from your description. You can begin to clarify the matter by running the following diagnostic commands on the disk from Linux:

```

sudo fdisk -lu /dev/sdb
sudo parted /dev/sdb print

```

This assumes the disk is /dev/sdb; if it's something else, you'll have to adjust the value appropriately. Post the output here, beginning with a [noparse]```
[/noparse] string and ending it in [noparse]
```[/noparse], otherwise it'll be hard to read. It's possible that this output will provide enough information to offer a suggested solution, but it may take more rounds of diagnosis before a suggestion for a solution can be offered.

One more thing: *Do not* attempt to write to *any* partition on the disk, from *any* operating system, until the cause of the problem is known. At this point, writing to the disk could damage it further. Even utilities intended to repair disk problems can go hopelessly awry with problems like yours, so unless and until a human being understands the problem, writing to the disk is dangerous.

---

