---
title: "So fsck just deleted all my data... please help!"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Muntted on 2008-03-04
So I had a raid 5 that was coming up with superblock errors and I couldnt mount.
I had it suggested that I run fsck on the part the /dev/md0 but now it seems it has deleted everything.

Is there any chance whatsoever of getting this data back?

---

### Post by bumanie on 2008-03-04
Your best chance of retrieving your data is to burn a live cd of test disk from here [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
It is a partition and data recovery tool. If you have a hard drive that has been changed and formatted many times, it will be more difficult to retrieve anyhting, but it's worth a try.

---

### Post by az on 2008-03-04
Image the raid device.  Then data carve the files from the image.

You can try to data carve the files directly from the image if you don't have enough space, just mount the device read-only.

help.ubuntu.com/community/DataRecovery

Testdisk won't help, since this is not a partition issue but a borked filesystem.  You will be able to revoer much of your data by carving the files out instead of using the filesystem to get at them.  Use Photorec (from the tesdisk package) and/or foremost to carve out the files.

If you need a live cd to work on this, I suggest the ubuntu-rescue-remix.  ([http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org))

---

### Post by Muntted on 2008-03-04
The only thing I have done to the raid drives (there were 2 of them so it was degraded) was to run fsck.

Any other options?

---

### Post by Muntted on 2008-03-05
Thanks first of all for responding to my thread, i really really appreciate it.

The raid that I was having problems with was running in a degraded mode (2 out of 3 disks) when fsck was run. Can I still use the procedure outlined?

If I can still do it, I run gddrescue to make an image of the raid device. It says on the guide that I will need more room on the new disk then on the failed one. Does this mean, more room as in overall or more room as in room taken up by data originally?  In this case there was 3 500gb disks, so there will be 1tb of space on the raid with about 400gb used up.

Also, I see with gddrescue you have to specify the type of filesystem. I originally made the filesystem ext3 but i think as people tried to help me we may have turned the filesystem into ext2 (if theats even possible).

I see the other option is to mount the raid in read only and try to use foremost on that. How exactly do I mount as read only? Will this have as high of a success rate. Will I need as much space as the raid again?

Should I use scapel or foremost?

---

### Post by az on 2008-03-06
> **Muntted said:**
> Thanks first of all for responding to my thread, i really really appreciate it.

The raid that I was having problems with was running in a degraded mode (2 out of 3 disks) when fsck was run. Can I still use the procedure outlined?

You are imaging the raid array as a block device, not as individual drives.  You should image the raid array before you make any changes to it. So however it was running when it failed, use that.  

> **Muntted said:**
> 
If I can still do it, I run gddrescue to make an image of the raid device. It says on the guide that I will need more room on the new disk then on the failed one. Does this mean, more room as in overall or more room as in room taken up by data originally?  In this case there was 3 500gb disks, so there will be 1tb of space on the raid with about 400gb used up.
The image will be the total size of the array, not just the space used.
> **Muntted said:**
> 

Also, I see with gddrescue you have to specify the type of filesystem. I originally made the filesystem ext3 but i think as people tried to help me we may have turned the filesystem into ext2 (if theats even possible).
No you don't.  It's a bit-for-bit copy.  It's filesystem agnostic.

> **Muntted said:**
> 
I see the other option is to mount the raid in read only and try to use foremost on that. How exactly do I mount as read only? Will this have as high of a success rate. Will I need as much space as the raid again?

Should I use scapel or foremost?

If a drive is physically dammaged, you will have trouble reading it.  This is where gddrescue is useful.  If hardware problems are not an issue, just do that.  Yes, it will save on space.  Well, if there are a lot of deleted files lying around on your filesystem, it will find them and copy them.  Where the filesystem was empty, it will not have anything to copy.

---

