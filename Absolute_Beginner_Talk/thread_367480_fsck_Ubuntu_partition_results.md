---
title: "fsck Ubuntu partition results"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by xyz on 2007-02-22
Hi everyone,
I need a little help with this output. 
For those who may also be interested in running this test, remember you need Ubuntu Live CD -that way the test is run on unmounted partitions-. Once you booted on the Live CD, open a terminal and run>
```
sudo -s
```
You need to be root to run fsck.
And then>
```
fsck -rfc /dev/hdax
```
Replace the  x  with your own.
A reminder...to find out what your  hdax is, run>
```
sudo fdisk -l
```
Do this when your partitions are mounted - not when you booted on the Live CD...obviouly.


From what I understand 3% non-contiguous is nothing to worry about. Nevertheless, the number keeps on growing over time.
*Can I do anything to lower that number?*
other than [Defragmenter for Linux]("http://ubuntuforums.org/showthread.php?t=169551&highlight=defrag")
Anybody knows of a different way to do it....for some reason I do not really trust that script. Don't ask me why, I don't know why.
Thanks for reading.

> ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# fsck -rfc /dev/hda2
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Checking for bad blocks (read-only test): done                        359
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/: ***** FILE SYSTEM WAS MODIFIED *****
/: 149709/1281696 files (3.0% non-contiguous), 1047544/2560359 blocks


---

### Post by esaym on 2007-02-22
Does that program tell you which files are fragmented?

---

### Post by xyz on 2007-02-22
> **esaym said:**
> Does that program tell you which files are fragmented?

I'm not sure I understand what you mean by "program"?
You mean this from the fsck output:
> /: ***** FILE SYSTEM WAS MODIFIED *****
/: 149709/1281696 files (3.0% non-contiguous), 1047544/2560359 blocks
or are you talking about the defragmenter link I posted above?
Thnx.

---

### Post by esaym on 2007-02-22
> **xyz said:**
> 

or are you talking about the defragmenter link I posted above?
Thnx.

Yea either with that defragmenter or with some other program.  I remember a thread where a bunch of people were complaining about non continuous files and somehow they were able to view which files they were. From what I remember, most of the files that were causing the high non continuous reading were log files and giant movie files.

---

