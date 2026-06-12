---
title: "Questions about switching - filesystem"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by 2_of_8 on 2007-08-21
I've tried several versions of Linux in the past, and while most of it was very good, there were certain things that made me go back to Windows. Here I am, wanting to switch again, but I would like to know more about the last thing that's stopping me: **filesystems**.

I'm on WinXP and obviously using NTFS. How will Ubuntu handle this? I have 4 partitions right now: Windows, Music, Movies, Other. 2 partitions per physical drive.

The Music partition is 120gb: will this pose a problem? Will I need to split it up into smaller ones? I get the feeling that I'll need to convert to a different filesystem; if so, how would I go about it - make a backup of everything, convert, copy back?

---

### Post by logos34 on 2007-08-21
If there's no unallocated space on either drive you'll have to shrink them to make room for linux.  Need at minimum 4GB of disk space -- a 256MB-1GB swap partition and rest for root partition.  Use ext3 filesystem for linux.  Consider getting [ntfs-3g driver]("http://www.ntfs-3g.org/") to save/write to NTFS partitions, and [fs-driver]("http://www.google.com/url?q=http://www.fs-driver.org/download.html&sa=X&oi=smap&resnum=1&ct=result&cd=1&usg=AFQjCNEL5II1dCISPldJZ-7UKp2j-xhLQA") to add r+w ext2/3 support to windows side.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by 2_of_8 on 2007-08-21
I have some unallocated space, and plenty of space to shrink.

I don't even think that I need to dual-boot. The one thing that I see as most problematic is running Half Life on linux. However, from a few threads that I've read here, it should be possible.

I've heard many things about NTFS support being iffy with Windows. Is this the case with the two drivers you listed? If so, would it make sense for me to switch partitions?

---

### Post by Frak on 2007-08-21
If you mean NTFS support being iffy with Linux, its pretty stable now, and should work flawlessly.

---

### Post by mikewhatever on 2007-08-21
The file system in Ubuntu is as good as ntfs and some may say even better. You do not split or convert partitions to a different file system, but resize (shrink one of the existing ones) to get unallocated space. In that space, the partitions for Ubuntu are created with the appropriate file system. In order to resize a partition, it is not necessary to move the file off of it, but is advisable to backup everything important. I really do not see what is stopping you. Perhaps some nice pictures will reassure [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Ek0nomik on 2007-08-21
If you don't want to keep Windows any longer then you could just reformat your Windows partition to EXT3 and install Ubuntu on it.  Then you could use the file system of your choice on your other partitions that store your media / data.  If you are using only Ubuntu, or another Linux distribution, then EXT3 would probably be the best.  You can also use FAT32 or NTFS, but as already mentioned you need third party support for NTFS.

I am not sure about size restrictions in regards to NTFS, but I know partitions can be as large as 8TB with FAT32 and [here]("http://en.wikipedia.org/wiki/EXT3#Size_limits") are the limits for EXT3.

---

