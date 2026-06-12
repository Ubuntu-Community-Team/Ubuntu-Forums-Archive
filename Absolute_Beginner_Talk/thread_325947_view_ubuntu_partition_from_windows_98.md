---
title: "view ubuntu partition from windows 98?"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by Jareth on 2006-12-26
just wondered if its poss? I had a job starting up the ubuntu partition today and while doing it thought it would be a good idea to have a way of getting at stuff in ubuntu through windows.

Much obliged!

---

### Post by Sef on 2006-12-26
> just wondered if its poss? I had a job starting up the ubuntu partition today and while doing it thought it would be a good idea to have a way of getting at stuff in ubuntu through windows.


If you have a FAT32 partition then both 98 and Ubuntu could read and write to the files.

---

### Post by merlyn on 2006-12-26
Hi,

it's definately possible. There is a product from Paragon called ext2fs Anywhere. Check this [site]("http://www.ext2fs-anywhere.com/").

It's a proprietary app that runs on Windows and allows ext2/3 partitions  to be mapped as a drive.

I'm not aware of any open source solutions sorry, so I guess it comes down to how badly you need this functionality, and whether you're willing to pay for it.

Either that or you can share data via a fat32 or ntfs partition, just check out this [thread]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs"), which describes how to set up ntfs rw access.

Wait a minute I just noticed a link to this [site]("http://fs-driver.org/index.html") on the thread I mentioned above, for a freeware utility that enables access to ext2 & 3 partitions from Windows.

You could check it out.

Cheers.

---

