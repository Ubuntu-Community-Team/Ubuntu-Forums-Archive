---
title: "gz and bz2"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by Ubuntuud on 2006-04-12
What is the difference between .tar.gz and .tar.bz2 files? I noticed that bz2s are smaller, but does that mean a quality loss? Thanks in advance!

---

### Post by ssalman on 2006-04-12
they are different compression algorithms, and different algorithms will attain different compression ratios.

With gz, bz2, rar and zip (among others), you don't lose any quality, as they are loosless (or perfect) compression algorithms. Unlike the mp3, jpeg compression where you do lose some of the data therefore some of the file quality due to compression.

hope this helps! :D

---

### Post by izmaelis on 2006-04-12
Yes, if you archive same file with both gz and bz2 the one made with bz2 (bzip2) will be smaller, but the main disadvantage of bzip2 is that it's MUCH slower and MORE resource hungry than gzip.

---

### Post by zerhacke on 2006-04-12
[QUOTE=Ubuntuud]What is the difference between .tar.gz and .tar.bz2 files? I noticed that bz2s are smaller, but does that mean a quality loss? Thanks in advance![/QUOTE]
There is no quality loss.  They're just different ways to compress files.  Consider them equivalent to RAR versus ZIP in Windows.  Both do not lose any data when they compress the files.  They just compress them different ways.

In other words, listen to ssalman.

---

### Post by Ubuntuud on 2006-04-12
OK. Thanks!

---

### Post by YuHoo on 2006-04-12
I assume that you probably know how to untar the different file types, but in case a beginner reads it you need to use -xz for .tar.gz and -xj for .tar.bz2

---

### Post by Ubuntuud on 2006-04-12
I use fileroler...

---

