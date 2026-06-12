---
title: "Largest file size?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by justinae on 2007-05-10
Does Ubuntu have a file size limit? I have a large movie file (25Gig). I'm running 7.04 and partitioned the hard drive as one large drive during install.

thanx

---

### Post by Nekiruhs on 2007-05-10
Not as far as I know.

---

### Post by Najand on 2007-05-10
As far as I know with EXT3, it is 8TB, (i.e. 8192 GB)

---

### Post by Bachstelze on 2007-05-10
It depends on the block size of your filesystem. For 1 KiB blocks, the max file size is 16 GiB, for 2 KiB blocks, it's 256 GiB and for 4 KiB and 8 KiB blocks, it's 2 TiB.

It may sound large but it's actually relatively small compared to other filesystems.

---

### Post by Pragmatist on 2007-05-10
> **justinae said:**
> Does Ubuntu have a file size limit? I have a large movie file (25Gig). I'm running 7.04 and partitioned the hard drive as one large drive during install.

thanx

To my knowledge, there is no file size limit on Linux.  You can impose file size limits if you want to using the **ulimit** command.  This would typically be done by a system administrator to insure that disk space is preserved.  In fact, my guess is that ulimit isn't part of the default distribution of Ubuntu as I don't have it installed.

Check this out: [http://www.cyberciti.biz/faq/file-size-limit-exceeded-error-under-linux-and-solution/](http://www.cyberciti.biz/faq/file-size-limit-exceeded-error-under-linux-and-solution/)

Specifically this line:
> If you do not want any limit remove fsize from /etc/security/limits.conf.

---

### Post by Najand on 2007-05-10
It is still bigger than FAT32!

---

### Post by heimo on 2007-05-10
And the block-size by default depends on the size of the partition, as far as I know. For all of my partitions block-size is 4k - you can check this by using 
```
sudo dumpe2fs -h  /dev/sda1 | grep -i "block size"
```
where sda1 is your partition

---

### Post by heimo on 2007-05-10
> **Pragmatist said:**
> To my knowledge, there is no file size limit on Linux.

To my knowledge, there definitely are filesize limits - however these are getting less relevant to most users. Limits are different for different filesystems, and even architecture dependent.

---

### Post by Jaza on 2007-05-10
With larger files it would be wise to use xfs or jfs filesystems, but for info of max file size check:
[http://en.wikipedia.org/wiki/Comparison_of_file_systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")

---

### Post by justinae on 2007-05-10
Here is the ouput:

euts@euts:~$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) unlimited
max locked memory       (kbytes, -l) unlimited
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) unlimited
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

if file size is unlimited does that REALLY mean unlimited, as in i can have a 25Gig file?

thanx for all the help for a newbie. i'm loving ubuntu so far!

---

### Post by Bachstelze on 2007-05-10
Some people with a bit more knowledge have already answered you, follow their advice instead ;)

(and w00t for the 3000th message !!)

---

### Post by Pragmatist on 2007-05-11
> **heimo said:**
> To my knowledge, there definitely are filesize limits - however these are getting less relevant to most users. Limits are different for different filesystems, and even architecture dependent.

My mistake. Thank you for the correction.  So, to make sure I'm coming to the right conclusion, if the block size is 4k, then on an ext3 file system the maximum file size is 2 Terabytes?  I've arrived at this conclusion from these wikipedia links (the first was posted above):
[http://en.wikipedia.org/wiki/Comparison_of_file_systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems#fn_4")

Then for the ext3 file system:
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

If this is correct, then the OP's 25GB file is only a problem if his/her block size is 1K.  This assumes the OP is using ext2 or ext3.  With JFS, XFS, ReiserFS it shouldn't even be a problem with 1K block size.  However, if the file system is FAT32 it looks like 25GB is well over the 4GB file size limit.

If this summary is incorrect, please provide a more accurate one.

---

### Post by heimo on 2007-05-11
Yeah, I think your summary and analysis is thorough and correct. Thanks!

---

### Post by justinae on 2007-05-12
After several hours, the large files (25gig) were copied onto the ext3 partition with no problem.

thanx for all the help!

---

