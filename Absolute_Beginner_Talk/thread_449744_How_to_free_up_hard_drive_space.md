---
title: "How to free up hard drive space?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by e^(i*pi) on 2007-05-20
I only have 1.4 gigs of available space on my Ubuntu partition, and I am wondering if any of you know any good methods for freeing up some additional space.  Any ideas will be greatly appreciated.

---

### Post by Klargodut on 2007-05-20
I asked a similar question some day ago in this thread, and got the answer that the root user had plenty of reserved space in case some malicious process would eat up all other free space. I decided to reduce the space root got from 1 GiB to 100 MiB by doing this:

```

emil@linux-laptop:~$ sudo tune2fs -r 26000 /dev/hda3
tune2fs 1.40-WIP (14-Nov-2006)
Setting reserved blocks count to 26000

```

[http://ubuntuforums.org/showthread.php?t=446525](http://ubuntuforums.org/showthread.php?t=446525)

---

### Post by e^(i*pi) on 2007-05-20
Cool, thanks.  I also realized that when I installed Ubuntu, I made my swap partition way way too big.  How can I resize things so that my swap is the right size and give the extra to my / partition?

---

### Post by jfinkels on 2007-05-20
> **e^(i*pi) said:**
> Cool, thanks.  I also realized that when I installed Ubuntu, I made my swap partition way way too big.  How can I resize things so that my swap is the right size and give the extra to my / partition?

Boot into the Live CD environment, and then use Gparted to resize your partitions as desired! It's in System > Administration > Gparted

---

### Post by e^(i*pi) on 2007-05-21
Thanks, I'll try that and let you know how it goes

---

### Post by mikewhatever on 2007-05-21
Try cleaning the /var/cache/apt/archives download cache. All programs and updates you download with apt-get are stored there.
> sudo aptitude clean

---

