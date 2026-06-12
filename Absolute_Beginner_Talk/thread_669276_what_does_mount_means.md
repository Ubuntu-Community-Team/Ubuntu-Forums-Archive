---
title: "what does mount means"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by coolnik6 on 2008-01-16
what is mounting a partition means???

also  when i use **free**e command it shows memory  in blocks not in MB or GB
so how i can  know  my free space in MB or GB
right click also doesn't work , it don't show  the size of folder or directory
how to make it out, how much is free
 its very confusing

---

### Post by eolson on 2008-01-16
free -m will give it to you in MBytes

to answer the mount question,  it's probably easiest if you open a terminal and

   man mount

---

### Post by Cypher on 2008-01-16
Mounting a partition makes it available for use. The directory to which a partition is mounted to is your "view" into that particular. It can be ANY directory you want..

A few of the directories have special meaning like "/", "/usr" and so on..but you could mount your CD under "/home/<username>/mysuperdupercd" if you wanted..

You can change the way "free" reports the available memory by using "free -k", "free -m" and "free -g" to report in KB, MB and GB..

When in doubt...
```

man <command>

```
Where <command> in this case would be 'free'.

---

### Post by xxLONESTARxx on 2008-01-16
For a good definition of mounting, take a look at this link:

[http://www.ibm.com/developerworks/linux/library/l-linux-filesystem/?ca=dgr-btw01LinuxFileSystAnat&S_TACT=105AGX59&S_CMP=GR](http://www.ibm.com/developerworks/linux/library/l-linux-filesystem/?ca=dgr-btw01LinuxFileSystAnat&S_TACT=105AGX59&S_CMP=GR)

Maybe I misunderstood your other question but, isnt Free Commander a Windows file manager?

EDIT: OK, I was confused about the whole "free" command...I admit I'm a bit of a n00b :)

---

### Post by whitewizardcoder on 2008-01-16
mounting a partition makes it readable as a directory in the file system.  It's essentially the same thing as lettered drives (A:, c:, ...) in windows.  The partition with Ubuntu on it is mounted at '/', the root of the filesystem.  If you have another partition, you can mount it anywhere inside the filesystem, such as '/media/hddisk'.  To see how mounting works, type 'man mount' into a terminal.  You can also unmount a partition using 'umount'.

To display the free memory in mb or gb, type 'free -m' or 'free -g' into a terminal.  if you want to find out more about free, or for that matter any command in linux, just type 'man free', replacing free with whatever command you're trying to use.

---

### Post by dstew on 2008-01-16
The word "mount" comes from the old days when you had to physically put a big tape reel onto the spool in one of the tape drives that were as big as phone booths, or put a trash-can-lid-sized disk cartridge into a washing-machine-like disk drive. In those days, mounting a file system used up some human calories as well as electric current!

---

