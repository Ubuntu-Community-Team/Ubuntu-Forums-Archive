---
title: "Can't right to hard drive?"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by GreenLantern33 on 2006-12-14
I have two hard drives in my computer the first one is a 300 gig that I have split in half between Windows and Ubuntu (6.10).  The second is a 500 gig hard drive that I keep all my music, pictures, movies, etc.

My problem is that in Ubuntu I can't write to the 500 gig drive.  How can I make it so that I can?

Thanks,
GL

---

### Post by Average Joe on 2006-12-14
Depends on the file system of the drive. What is it? ext3, fat32, or ntfs (or something else)?

---

### Post by GreenLantern33 on 2006-12-14
It's either fat32 or NTFS.  Is there a quick way to find out for sure?

---

### Post by bodhi.zazen on 2006-12-14
```
sudo fdisk -l
```

---

### Post by GreenLantern33 on 2006-12-14
Ok it's NTFS 

Actually it says HPFS/NTFS, is that the same thing?

---

### Post by taurus on 2006-12-14
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by mcduck on 2006-12-14
Support for writing to NTFS is not very reliable in Linux, as it's Microsoft's proprietary filesystem and they refuse to give any info about it..

There are some tricks to get it working, and many people say that they work fine but if your files are of any value to you I'd recommend against that.

---

### Post by bodhi.zazen on 2006-12-14
> **GreenLantern33 said:**
> Ok it's NTFS 

Actually it says HPFS/NTFS, is that the same thing?

Yes, the partition is NTFS

To enable reaad-write access try ntfs-3g: 

[http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support](http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support)

Be warned there is a small risk you will toast the partition.

FAT is a better format for shared partitions.

You would then mount with:

```
sudo mount /dev/hdxy /mount/point -o umask=000
```

---

### Post by GreenLantern33 on 2006-12-14
> **mcduck said:**
> There are some tricks to get it working, and many people say that they work fine but if your files are of any value to you I'd recommend against that.

Well the files that I have on the 500gb drive are of extreme value to me.  I think what I'm going to do is wipe the windows part, copy everything from the 500gb drive to the newly wiped windows drive, then format the 500 gb to ext3, and finally copy everything back to it.

Sound like a plan?

---

### Post by taurus on 2006-12-14
Then this link is for you...

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by mcduck on 2006-12-14
That sounds like a good way of doing it. And there are some Ext drivers for Windows that work very well, if you need to access those files from Windows some day.

---

### Post by taurus on 2006-12-14
> **mcduck said:**
> That sounds like a good way of doing it. And there are some Ext drivers for Windows that work very well, if you need to access those files from Windows some day.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

