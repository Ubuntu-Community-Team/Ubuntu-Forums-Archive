---
title: "HFS+, limit on number of files in directory, and photorec"
date: 2012-11-08
forum: Apple Hardware Users
---

### Post by skullmunky on 2012-11-08
Does linux HFS+ put a limit on the number of files you can create in a directory?

I'm using photorec to try and recover documents off the HFS+ partition on my triple-boot macbook. I'm storing recovered files onto an external drive which is also formatted HFS+.  Both are non-journaled.  

I would, obviously, prefer to store the recovered files on an ext3 drive, but I've been having some kind of frustrating problem formatting large external drives ext3, so as a Mac/Linux user I've just been using HFS+ for my external storage without any issues so far.

Anyway, photorec did a great job, found lots of deleted files (way more than the $80 Mac utility I bought to try and do the same thing!) but I think it stopped before it was done.  I have exactly 999 recovery directories, named recup_dir.1 through recup_dir.999.  Strangely, I cannot create any more files or directories in the directory where all those recup_dir's are:

```

find . -name *.xlsx > excel.txt
bash: excel.txt: No such file or directory 

```

same with touch, mkdir, pico, etc.  So I'm wondering (a) if photorec stopped early, and (b) is there something about HFS+ that won't let it make more than 1000 files in a directory?  (I know there isn't a limit like that normally, but is there one accidentally in the linux implementation or something?)

---

