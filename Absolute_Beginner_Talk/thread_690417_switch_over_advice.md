---
title: "switch over advice"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by tone33 on 2008-02-07
So I installed Ubuntu a few days ago and have it up and running - I can play music, watch videos, etc.  It's all great!  Now I'm thinking about a total switchover (well, except for my work which is .NET development) and I'm looking for advice on how to handle existing music, video and pictures that are stored on a NTFS partition.  I installed Ubuntu on a ext3 partition.  So my questions are:

1) I've heard of a new package that allows Linux to read AND write to NTFS - does this package hold any weight (no file corruption, good access times, etc) ?  

2) Is there a way to "convert" the files from NTFS to EXT3, if so can they be "converted" back?

Thanks.

---

### Post by emarkd on 2008-02-07
1.  Never used it, sorry.

2.  The files aren't in that format, your disk is.  If you copy the file from Windows to Ubuntu, it'll automatically be converted when Ubuntu stores it on it's ext partition.  If you're asking if you can convert the entire partition/disk, you can't without formatting it and losing it's contents.

---

### Post by Mogurijin on 2008-02-07
If you are using the latest Ubuntu, this will already be installed. If not you will have to go get it from the repository. Search for "NTFS" it will show up.

Also, when using 7.04 (which I had to install the program on) I had no issues with this program. Such as with corruption. I found it worked surprisingly well.

I hope this helps.

---

### Post by fiddledd on 2008-02-07
> **tone33 said:**
> So I installed Ubuntu a few days ago and have it up and running - I can play music, watch videos, etc.  It's all great!  Now I'm thinking about a total switchover (well, except for my work which is .NET development) and I'm looking for advice on how to handle existing music, video and pictures that are stored on a NTFS partition.  I installed Ubuntu on a ext3 partition.  So my questions are:

1) I've heard of a new package that allows Linux to read AND write to NTFS - does this package hold any weight (no file corruption, good access times, etc) ?  

2) Is there a way to "convert" the files from NTFS to EXT3, if so can they be "converted" back?

Thanks.


1) If you mean ntfs-3g it works out of the box in Ubuntu (7.10). I used it to r/w to NTFS for about 6 minths with no data loss etc. One caveat though, make sure you don't save files to NTFS with illegal characters. I saved a Webpage with the default page title (i'm lazy) and coudn't access it in XP. Had to rename in Ubuntu. Also rememeber that ntfs-3g is stable but AFAIK still being developed.

2) Not sure what you mean

---

### Post by bodhi.zazen on 2008-02-07
Actually, the package that allows rw access to ntfs is ntfs-3g (ntfs is ro).

You can configure it easily with ntfs-config : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

I have seen rare problems with ntfs-3g, in which case one needs to boot to windows to fix it. This is not a problem if you use windows.

If you give up windows, best to convert your NTFS partition to a linux native file system, ext3, reiserfs, jfs, xfs ...

You can not convert a partition ntfs -> ext3 -> ntfs without formatting. If you format a partition you will lost the data, so back up to CD/ DVD or another partition first.

---

### Post by ugm6hr on 2008-02-07
> **tone33 said:**
> 1) I've heard of a new package that allows Linux to read AND write to NTFS - does this package hold any weight (no file corruption, good access times, etc) ?  

2) Is there a way to "convert" the files from NTFS to EXT3, if so can they be "converted" back?

As mentioned - *ntfs-3g* is the package, and is default installed in Gutsy.  You can just use that to access your media files where they are.

If you want to reformat to ext3, you would have to backup all the files, reformat, and copy them back.  This is fully reversible (by the same process).

You can also access ext3 from XP with [http://www.fs-driver.org/](http://www.fs-driver.org/) (in the same way that ntfs-3g allows NTFS access from Linux).

Your choice!  I dual-boot (rarely in XP), with an ext3 "storage" partition.

---

### Post by stchman on 2008-02-07
> **tone33 said:**
> So I installed Ubuntu a few days ago and have it up and running - I can play music, watch videos, etc.  It's all great!  Now I'm thinking about a total switchover (well, except for my work which is .NET development) and I'm looking for advice on how to handle existing music, video and pictures that are stored on a NTFS partition.  I installed Ubuntu on a ext3 partition.  So my questions are:

1) I've heard of a new package that allows Linux to read AND write to NTFS - does this package hold any weight (no file corruption, good access times, etc) ?  

2) Is there a way to "convert" the files from NTFS to EXT3, if so can they be "converted" back?

Thanks.

You need to mount those NTFS partitions.  I have a tutorial on that.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

Yes, ntfs-3g works well.  I have never had any problem with it.

---

### Post by tone33 on 2008-02-07
Thanks for all the feedback - my questions were answered.

I have one more question.  Is there an efficiency advantage to the Ext3 filesystem vs NTFS?

---

### Post by emarkd on 2008-02-07
As for efficiency, I'm not sure, but ext3 has one thing going for it that ntfs never will have:  it's open source.  Since ntfs is a proprietary microsoft technology, the Linux community is stuck trying to reverse-engineer it to even make it accessible and that'll never change.  Ext3 is an open format, so you'll always be able to get to your data no matter what OS you're using.

---

### Post by tone33 on 2008-02-07
ok cool.  that's one reason I want to switch.  I'm tired of being married to Microsoft.  Even though I work in .NET development and Microsoft does a lot of things right, some things they just can't do because they are proprietary.  And the support on these forums kills anything I've seen on windows forums.

---

### Post by emarkd on 2008-02-07
Agreed, the community is one of Ubuntu's strongest assets.  It's even much better than other F/OSS projects and Linux distros.

I also have to do a bit of .NET developing on occasion.  I wish MS would follow through with their promise and actually contribute to the Mono project, but since that's pretty unlikely I'll keep XP around for .NET that I have to do.  But for my own projects and ideas, I'll never code a line of those in .NET because I can't trust my code to MS whims and lock-ins.

---

