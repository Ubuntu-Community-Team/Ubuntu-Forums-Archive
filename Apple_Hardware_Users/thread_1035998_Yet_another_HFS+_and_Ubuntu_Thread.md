---
title: "Yet another HFS+ and Ubuntu Thread"
date: 2009-01-10
forum: Apple Hardware Users
---

### Post by hg2491 on 2009-01-10
I know, I know.. This has been asked plenty of times, but I still do not understand how to proceed. I have an external hard drive formated with HFS+ and need Ubuntu to be able to write to it.

Thanks in advanced,
Hg+

---

### Post by tiresia on 2009-01-10
It is quite easy: 

1. Parted cannot generate a HFS+ Partition
2. Parted can ***resize*** (shrink) a HFS+ Partition
........
3. Linux can read any HFS+ Formatted Partition
4. Linux can write on any HFS+ ***not Journaled*** Formatted Partition
.......
As you can see, the point is _to disable journaling_. You can do it in MacOSX with diskutil. Start a Terminal in MacOSX and run:
```
# diskutil disableJournal /Volumes/TheVolumeName
```

---

### Post by hg2491 on 2009-01-10
What are the repercussions of disabling journaling? Can I do this from Ubuntu? I do not have a Mac around right now.

Thanks for all the help,
Hg+

---

### Post by mkvnmtr on 2009-01-10
I keep my external hard drive formated hfsplus the same as hfs+ so I can read and write in both Mac and Ubuntu. I formated with disk utility in Mac. It is very easy to see whether you are making the partition journaled or not. My partition editor in Ubuntu says it can not make a hfs+ partition. If it is not an external drive you will probably need a Mac install disk. There might be a linux diskn that has the utilities to do it but I haven't heard of it.

---

### Post by zachthejones on 2009-01-11
I need to be able to write to an HFS+ initialized iPod. will diskutil work for that? I couldn't find it in the regular archives, where did you get it from?

---

### Post by mkvnmtr on 2009-01-11
Disk Utility is on your Mac. It is also on your mac install disk. You can use it to form the hfs+ partition. Then when you get your permissions correct you can write to the partition in Ubuntu. Of course you can write to it from Mac. The Ubuntu tool GParted will not form the partition in hfs+. It will resize it after it has been formed. There may be some cross platform apps that will be useful that you can install from the package manager in Ubuntu but that is for after you have your partition up and running.

---

### Post by zachthejones on 2009-01-11
ah, gotcha. I'm running ubuntu installed on an ex-windows laptop (much better now, thank you!). so that's why I don't have it. But no sweat, think I got my problem worked out in a different way...thanks anyways!

---

### Post by cyberdork33 on 2009-01-11
> **hg2491 said:**
> What are the repercussions of disabling journaling? Can I do this from Ubuntu? 
no you cannot do it from Ubuntu.

[http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)

---

