---
title: "what is the best filesystem"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by youthforlinux on 2006-05-24
what is the best filesystem for ubuntu and why and why aren't the other ones

---

### Post by 23meg on 2006-05-24
You'll get varied answers, because there's not a single best filesystem for all purposes. If you do a forum search you'll find many threads where this was discussed. For general use EXT3 and ReiserFS will do fine.

---

### Post by youthforlinux on 2006-05-24
[QUOTE=23meg]You'll get varied answers, because there's not a single best filesystem for all purposes. If you do a forum search you'll find many threads where this was discussed. For general use EXT3 and ReiserFS will do fine.[/QUOTE]

what is difference between EXT3 and ReiserFS anyways?

---

### Post by mlind on 2006-05-24
well, you got atleast options EXT2, EXT3, XFS JFS and ReiserFS.

I have good experiences with ReiserFS while I was using SuSE, it was fast and
performed well on workstation use. I've got no experience whatsoever on XFS or JFS.

Ext3 is rock solid and performs good on workstation or server use. It's mature and
maybe that's why it's preferred. dunno. Ext2 is like ext3 without journalling.

If you setup your system using LVM, it's easy to create new partitions with desired
filesystems and test things out yourself.

my two cents.

---

### Post by skippy81 on 2006-05-24
I use XFS for my home and root systems, and ext3 for my boot partition.   ReiserFS is good for loads of small files, ie a web or email server.  

XFS is good for larger files, and is a particular favourite for media center PCs.

Both ReiserFS and XFS should in theory give you a slightly quicker system than Ext3, but the difference is negligable for day to day use.  XFS cant be used as a boot partition AFAIK, so if you wanted to use it you would have to seperate /boot from the rest of your filesystem.   Not sure if Reiser has the same restriction.  

I would love to know which filesystem is best for the linux root system though, I assume it is Reiser since most of the files are fairly small.

---

### Post by youthforlinux on 2006-05-24
oh okay

though does anyone know about XFS or JFS and why anyone would use them

---

### Post by mlind on 2006-05-24
I bet google knows something ;) 

[http://linux.org.mt/article/filesystems](http://linux.org.mt/article/filesystems)
[http://jamesthornton.com/hotlist/linux-filesystems](http://jamesthornton.com/hotlist/linux-filesystems)
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

---

### Post by youthforlinux on 2006-05-24
sweet maybe ill use reiserFS then

---

### Post by glinsvad on 2006-05-24
[QUOTE=mlind]I bet google knows something ;) [/QUOTE]

Don't they ever... they have constructed their very own filesystem called GFS :rolleyes:

---

### Post by youthforlinux on 2006-05-24
what is GFS????

---

### Post by richbarna on 2006-05-24
GFS is a file system designed by Google.
Google is an amazing search engine that can find answers to even the smallest of questions.
No really, you should try it.
I normally use it to find answers to stuff before I post on the forum, but that's just me, I am a sucker for finding my own information.
It makes me feel good to know that at least I tried before I asked someone else. :)

---

### Post by youthforlinux on 2006-05-24
haha
i trust the ubuntu community

---

