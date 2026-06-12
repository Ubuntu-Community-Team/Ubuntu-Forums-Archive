---
title: "EXT2 to EXT3 filesystem"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Gerry Atric on 2006-10-08
I have Ubuntu Dapper installed on /dev/sdb8  under the EXT2fs formatted file system. I have been getting a lot of power outages and want to convert my Dapper partition to EXT3fs formattting to prevent loss of data.
I have read that a partition can be converted by using the command 
tune2fs -j and then apparently unmounting the /dev/sdb8 partition and remounting it.
Where does it need to me mounted and how?
Can someone knowledgable please advise me the correct code and sequence for doing this and very importantly will converting the file system destroy any data on the /dev/sdb8 partition.
Full explanation please as I am still staggering/blundering in Ubuntu Linux.

---

### Post by po0f on 2006-10-08
Gerry Atric,

[Click](http://www.troubleshooters.com/linux/ext2toext3.htm).

If your install of Ubuntu is on this partition, use a live cd to boot up and follow those directions.  It's not a good idea to be playing with a live filesystem while making fundamental changes to how it works.  While your at it, use [this guide](http://forums.gentoo.org/viewtopic-t-305871.html) to get a little more performance out of ext3.  ;)

And remember, back up!  Though considered safe, converting any filesystem to another one may fail.

---

### Post by Gerry Atric on 2006-10-08
Brilliant, info much appreciated. Thanks.

---

