---
title: "Journaled file system, writable from Ubuntu and Mac Os X?"
date: 2008-05-17
forum: Apple Hardware Users
---

### Post by 2cute4u on 2008-05-17
I am dual booting Ubuntu and Mac OS X,.  The problem is that ext2 partitions have to be unjournaled to be writable in OS X and HFS+ partitions have to be unjournaled to be writable in Unbuntu. Now but every time I go back and fourth, i have to wait for my my unjournaled partitions to be rechecked.  Is there a journaled file system, that I could use, that is writable in both OS's?

---

### Post by cyberdork33 on 2008-05-17
ext3 should be writable from OSX (though it has been giving trouble recently).

ZFS is probably a good solution to this, but I don't think it is supported in Linux quite yet because of license restrictions.

[http://zfs-on-fuse.blogspot.com/](http://zfs-on-fuse.blogspot.com/)
[http://zfs.macosforge.org/trac/wiki/downloads](http://zfs.macosforge.org/trac/wiki/downloads)

---

### Post by 2cute4u on 2008-05-18
> **cyberdork33 said:**
> ext3 should be writable from OSX (though it has been giving trouble recently).

ZFS is probably a good solution to this, but I don't think it is supported in Linux quite yet because of license restrictions.

[http://zfs-on-fuse.blogspot.com/](http://zfs-on-fuse.blogspot.com/)
[http://zfs.macosforge.org/trac/wiki/downloads](http://zfs.macosforge.org/trac/wiki/downloads)


both ext3 and ZFS are read only on Mac OS X

---

### Post by cyberdork33 on 2008-05-18
> **2cute4u said:**
> both ext3 and ZFS are read only on Mac OS X
I have written to ext3 from OSX before. The driver is just not reliable.

Also, the driver I linked to for Mac seems to imply that you can write to a ZFS volume.

---

### Post by 2cute4u on 2008-05-18
> **cyberdork33 said:**
> I have written to ext3 from OSX before. The driver is just not reliable.

Also, the driver I linked to for Mac seems to imply that you can write to a ZFS volume.

How did you write to ext3?

When you say it's not reliable what do you mean?  I need something reliable and stable, that doesn't take hacking to get to work.

---

### Post by frog_pilot on 2008-05-18
with this utility [ext2fsx]("http://sourceforge.net/projects/ext2fsx") you will be able to read/write to ext3 from OSX. never heard about lacking reliability. [review]("http://forums.macrumors.com/showthread.php?t=88563").

The only thing, I experienced is sometimes it cant read the content of a folder. (I think it's due to journaling. When I open a subfolder deep in the folderhierarchy which I never opened from inside ubuntu there seems to be no content)

Try it out! You could start with an extra ext3-Volume for data sharing and mount /home and / read only for the first time, until you checked if write-support is reliable for you.

//edit: I use 1.1.3. In the recent version 1.4d3 the reading behaviour seems to be eliminated ([here]("http://sourceforge.net/forum/forum.php?forum_id=605876")) > A lot of work went into this release (the dir lookup offset caching was a particular pain in the ***), so please consider a Donation (see the Readme).

---

### Post by 2cute4u on 2008-05-18
> **frog_pilot said:**
> with this utility [ext2fsx]("http://sourceforge.net/projects/ext2fsx") you will be able to read/write to ext3 from OSX. never heard about lacking reliability. [review]("http://forums.macrumors.com/showthread.php?t=88563").

The only thing, I experienced is sometimes it cant read the content of a folder. (I think it's due to journaling. When I open a subfolder deep in the folderhierarchy which I never opened from inside ubuntu there seems to be no content)

Try it out! You could start with an extra ext3-Volume for data sharing and mount /home and / read only for the first time, until you checked if write-support is reliable for you.

//edit: I use 1.1.3. In the recent version 1.4d3 the reading behaviour seems to be eliminated ([here]("http://sourceforge.net/forum/forum.php?forum_id=605876"))

I have  [ext2fsx]("http://sourceforge.net/projects/ext2fsx") installed on my system, that's how I can read ext3 partitions, but they mount as read only.   [ext2fsx]("http://sourceforge.net/projects/ext2fsx") mounts ext2 as read write, but not ext3.

---

### Post by frog_pilot on 2008-05-18
It can also mount ext3 in r/w mode. The only difference between ext2 and ex3 is the journal. osx cant write to this journal but on mounting the volume from within linux, the journal will be recovered.

I am actually writing from OS X.4 to ext3 volume via ext2fsx.

Assume, you know that you can change acessibility of ext-volumes via prefrence panel... whats happennig if you choose to mount the volume r/w? Isnt it possible at all?

---

### Post by 2cute4u on 2008-05-18
> **frog_pilot said:**
> It can also mount ext3 in r/w mode. The only difference between ext2 and ex3 is the journal. osx cant write to this journal but on mounting the volume from within linux, the journal will be recovered.

I am actually writing from OS X.4 to ext3 volume via ext2fsx.

Assume, you know that you can change acessibility of ext-volumes via prefrence panel... whats happennig if you choose to mount the volume r/w? Isnt it possible at all?
There isn't a selection to mount r/w (that is the default behavior for ext2)  there are only 3 options:
Don't Automount
Mount Read Only
Ignore Permissions

All 3 of them are unchecked, and the volume mounts is  not writable.  

Maybe it's because you are using Tiger and I'm using leopard. or maybe you did something different then you are saying.

---

### Post by frog_pilot on 2008-05-18
ok you are right. mounting r/w is the default setting.

AFAIK ext2fs is for tiger. leo seems to be not supported: [bugreport]("http://sourceforge.net/tracker/index.php?func=detail&aid=1912513&group_id=64713&atid=508406")

---

### Post by cyberdork33 on 2008-05-18
yes I think it is a leopard thing too. That seems to be when people starting having issues with it.

---

### Post by volanin on 2008-05-18
It seems that EXT2FSX has some incompatibilities with the EXT2 flag DIR_INDEX.
To enable write permissions in MACOSX, first you have to unset it in linux:

tune2fs -O ^dir_index [partition]

Be aware though that EXT2FSX version 1.4D4 is unstable on the MACTEL.
Here, it crashed whenever you unmounted a read-write partition.
And that caused minor corruptions on the EXT2 filesystem.

EXT3 should work with no problems.
But I also heard that there is no support for Leopard.

---

### Post by frog_pilot on 2008-05-18
btw did you try to use hfs+ with journal disabled to share data between linux and osx. I'm using this with my volume for music. I have r/w access from linux and osx. Amarok is working fine on that volume and neither does itunes...

And there is another way. :lolflag: For my windoze-peers I have a ntfs external drive. And with the ntfs3g installed in osx and linux it works quite fine, but on this filesystem you have to deal with the problem of fragmented data. If you have much writing-access, you will run into big trouble, unless you have a windoze to defragment the volume periodic...

---

### Post by 2cute4u on 2008-05-20
> **frog_pilot said:**
> btw did you try to use hfs+ with journal disabled to share data between linux and osx. I'm using this with my volume for music. I have r/w access from linux and osx. Amarok is working fine on that volume and neither does itunes....

Yes, at the moment thats what I'm using now, that's the whole problem, that i mentioned in my original post.  Without journaling the whole file system needs to be rechecked at every reboot, and I've  had to wait as much as 5 minutes before the home partition is mounted so that I could log in. also without journaling there's more risk of data corruption if there's a crash.



> **frog_pilot said:**
> And there is another way. :lolflag: For my windoze-peers I have a ntfs external drive. And with the ntfs3g installed in osx and linux it works quite fine, but on this filesystem you have to deal with the problem of fragmented data. If you have much writing-access, you will run into big trouble, unless you have a windoze to defragment the volume periodic... I've never used windows, so if it requires windows, then it's not an option.

---

### Post by mchladek on 2008-05-20
I'm not very familiar with file systems, but have you considered UFS?  There is native support for it in OS X and according to [this post]("http://www.linuxforums.org/forum/ubuntu-help/115396-edit-kernel-support-ufs-read-write.html") over at Linux Forums, it should be easy to add read/write support in Ubuntu.

The only question is journaling capabilities.  I don't believe UFS uses journaling but some sort of metadata logging feature instead.  You may want to check out [this PDF]("http://www.sun.com/software/whitepapers/solaris10/fs_performance.pdf") from Sun, which gives some comparisons of ext3 and UFS.

---

### Post by flaggh on 2008-05-20
I use an unjournaled, case-sensitive, hfsplus partition to share files in ubuntu and os x and I am not experiencing this filesystem check every boot like you mention.  Could there be another reason it is triggering a filesystem check at every boot?

---

### Post by cyberdork33 on 2008-05-20
> **mchladek said:**
> I'm not very familiar with file systems, but have you considered UFS?  There is native support for it in OS X and according to [this post]("http://www.linuxforums.org/forum/ubuntu-help/115396-edit-kernel-support-ufs-read-write.html") over at Linux Forums, it should be easy to add read/write support in Ubuntu.

There is no support for _Apple's version_ of UFS in Linux. We have chased that rabbit before. It is a bit different than plain UFS.

---

### Post by frog_pilot on 2008-05-20
> **flaggh said:**
> I use an unjournaled, case-sensitive, hfsplus partition to share files in ubuntu and os x and I am not experiencing this filesystem check every boot like you mention.  Could there be another reason it is triggering a filesystem check at every boot?

dito

---

