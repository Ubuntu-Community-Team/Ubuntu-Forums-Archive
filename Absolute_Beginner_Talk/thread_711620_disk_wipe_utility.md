---
title: "disk wipe utility?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by rbrittner on 2008-02-29
ah **** i was trying to read the othe disk wipe posts but accidently hit enter.  so since this post is now on, can you please let me know how to wipe the dirve with GRUP installed.  I used to use G disk for windows and now i need a utility that I can boot off the floppy.  (or is there one installed on the ubuntu CD?

Anyways, thanks in advance

Ryan

---

### Post by Duck2006 on 2008-02-29
> **rbrittner said:**
> ah **** i was trying to read the othe disk wipe posts but accidently hit enter.  so since this post is now on, can you please let me know how to wipe the dirve with GRUP installed.  I used to use G disk for windows and now i need a utility that I can boot off the floppy.  (or is there one installed on the ubuntu CD?

Anyways, thanks in advance

Ryan

Do you meen GRUB?

---

### Post by rbrittner on 2008-02-29
Sorry, No I had ubuntu installed and did an update on my graphics driver and basically after hours of trying to fix it i'm at the point now that I just want to reinstall.  So in windows land I used a utility called G disk, which basically allowed me to wipe the hard drive.  It doesn't work in linux land so now I need a program that I can use to format the Hard drive.  Sorry for the confusion

Ryan

---

### Post by Moop on 2008-02-29
You can use Killdisk to wipe a drive. It has a version for floppy disks. [http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)

The live cd has a partitioner that will delete, create and format partitions. System-Administration-Partition Editor.

---

### Post by Dr Small on 2008-02-29
Gparted can erase your drive, but not while it is mounted.
Consider running Gparted from the livecd ;)

---

### Post by rbrittner on 2008-02-29
thanks guys i'll be doing it ASAP.  Thanks agian

---

### Post by Duck2006 on 2008-02-29
dban

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

Will do it also.

---

### Post by finer recliner on 2008-02-29
unix based OSs have a command called dd installed which is used to copy files bit by bit from one source to a destintation. a popular use for it is to copy all zeros to a drive (thus erasing anything on it).

```
dd if=/dev/zero of=/dev/hda
```
where  /dev/hda is the name of the disk you want to wipe.
run it as root. it will probably take a long time to complete.

please be VERY carefull with this command. make sure you know what you're doing before running.

---

### Post by harold4 on 2008-02-29
> **Duck2006 said:**
> dban

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

Will do it also.

+1

---

### Post by Duck2006 on 2008-02-29
> 
Code:

dd if=/dev/zero of=/dev/hda


Not for the faint hearted.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by dcstar on 2008-02-29
> **rbrittner said:**
> Sorry, No I had ubuntu installed and did an update on my graphics driver and basically after hours of trying to fix it i'm at the point now that I just want to reinstall.
..........

There is no need whatsoever to "wipe" a drive to be able to reinstall, just delete the partition.

The Ubuntu installer will overwrite all files on the partition it uses in the install process.

You are not in Windows land any more, leave all the old habits where they belong.

---

### Post by rbrittner on 2008-03-02
> **finer recliner said:**
> unix based OSs have a command called dd installed which is used to copy files bit by bit from one source to a destintation. a popular use for it is to copy all zeros to a drive (thus erasing anything on it).

```
dd if=/dev/zero of=/dev/hda
```
where  /dev/hda is the name of the disk you want to wipe.
run it as root. it will probably take a long time to complete.

please be VERY carefull with this command. make sure you know what you're doing before running.


Thank you, this was EXACTLY what I was looking for, G disk does the exact same thing.  Thanks again

---

