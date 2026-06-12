---
title: "Data Recovery"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Pizzarth on 2007-11-14
I'd like some help in recovering some data which I accidentally deleted. 

for some reason I have two things of the same external HDD in my /media.

the first is

"My Book"
and the second is
"My\ Book"

In setting up an apache server, attempting to get it to set the root directory as "My Book"(the first one. this wokrked btw, sort of. ) it set it to the second one "My\ Book". The first one wouldn't work without the escape sequence(I'm guessing it's still called an escape sequence) of "\ ". However, that is the drive of the second one, which only had one folder in it.

I'm sorry if that's confusing, but it's not the problem......


the problem is, in an attempt to solve this I stupidly ran
```

rm -R My\ Book 

```
from the /media folder. This began purging files on the drive that I wanted to keep. Files that I spent time collecting, and didn't have backups for. (along with some I did have backups for, but that's besides the point. Those I can recover fairly easily. )

After a second or so of rm running, I realized that this was way longer than it should take to clear some empty folders. (which was all "My\ Book" had in it)
and I promptly did ^C. 

Still, a significant amount of files got deleted. (my movie/music collection, some large(several gigs worth) software, and some odd files that I'd spent a lot of time collecting. (not actively, but they build up, and it's a big shame to lose them.)


A friend has explained to me that it was able to delete them so fast because it didn't really purge the files, it just deleted the headers, suggesting that hte files themselves were still salvageable.

[b][i]
So, I'm looking for a tool, or a technique, that would be able to bring back (if not a lot, a decent amount. hopefully all) of the files that have been deleted.[/b][/i]
they were on a fat32 formatted external harddrive. 

Thank you for your time/help

---

### Post by Sef on 2007-11-14
Check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") or [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12") to recover your data.

---

### Post by Pizzarth on 2007-11-14
Thanks for the fast reply.

I have looked at and tried them, but I'm afraid I didn't understand how to use them :(

testdisk I only got about as far as file view on the partition. I can see on the site that the'e's a repairfat selection, but I can't find it.

for TRK I used version 3.3 build 301.
didn't exactly know how to work it. I tried mounting the drive, didn't work too well. it kept asking for the type and when I ran

man mount

and looked for the vfstype or something like that, fat32 wasn't on there and I wasn't sure what to put.
I also tried ntfsundelete, that didn't work either.(I did it wrong)


review
-it's an external hdd
-it's one big FAT32
-has nothing to do with boot sectors.(as fas as I know at least :S)

if possible, some more instruction would be great.

---

