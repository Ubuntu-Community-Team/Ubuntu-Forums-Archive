---
title: "Filesystem"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2006-10-29
I am about to install ubuntu 6.06 on a 200gb HD but i already have Xp home with Ntfs and it is one partition.

What is the best file system to use for the instalation of ubuntu

And how to do it?

---

### Post by meng on 2006-10-29
ext3 seems to suit most people. Look here for some tips:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
I recommend you defrag in Windows before you start. Some folks recommend defragging multiple times to get the used space compacted.

---

### Post by dbott67 on 2006-10-29
Ubuntu uses the ext3 filesystem by default, and will allow you to create one by re-sizing your existing NTFS partition.  Most linux distros will also allow other types of filesystems like ext2, reiserFS, JFS, etc. to be used.

Just be careful when installing onto an existing partition.  Due to the fact that you will be re-sizing the NTFS partition, there is always the small possibility that something goes wrong, so PLEASE backup.

Here's a great tutorial: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

-Dave

EDIT: D'OH! Great minds think alike... beaten to the punch! :)

---

### Post by mahy on 2006-10-29
I personally find XFS to be the best one, but there's no way to access it from windows. The second best is ReiserFS. All the benchmarks show it's way better than ext3.

---

### Post by fasoulas on 2006-10-29
> **dbott67 said:**
> Ubuntu uses the ext3 filesystem by default, and will allow you to create one by re-sizing your existing NTFS partition.  Most linux distros will also allow other types of filesystems like ext2, reiserFS, JFS, etc. to be used.

Just be careful when installing onto an existing partition.  Due to the fact that you will be re-sizing the NTFS partition, there is always the small possibility that something goes wrong, so PLEASE backup.

-Dave

You said ubuntu uses ext3 by default so if i choose the first choise in the step 6 of instalation i will be ok 

or i have to use the gparter?

---

### Post by fasoulas on 2006-10-29
I want the best but also can access it from windows

---

### Post by qamelian on 2006-10-29
> **mahy said:**
> I personally find XFS to be the best one, but there's no way to access it from windows. The second best is ReiserFS. All the benchmarks show it's way better than ext3.
It depends on what is stored on the filesystem. Some perform better when the system contains predominantly small files. Others are optimal for large chunks of data. You really need to research each FS to see what they were designed for.

---

### Post by ewaguespack on 2006-10-29
then the only option is ext2/3, as none of the others will be accessible from windows.

if it is a non-root partition then you can use fat32.

---

### Post by fasoulas on 2006-10-29
Which filesystem perform faster?

And if isn't nesessary to have access from windows what other options do i have?

---

### Post by dbott67 on 2006-10-29
Performance varies as to the speed of the system (CPU, RAM, hard drive RPM, hard drive cache, etc.), the size and type of files to be stored, as well as the function of the computer (server vs. workstation; database vs. text vs. multimedia, etc.). 

However, you're probably best to stick with ext3, as that's what most of the community uses (strength in numbers when it comes to getting help).

---

### Post by mahy on 2006-10-29
> **ewaguespack said:**
> then the only option is ext2/3, as none of the others will be accessible from windows.

if it is a non-root partition then you can use fat32.

ReiserFS IS accessible from windows, using a plugin for Total Commander.

---

### Post by mahy on 2006-10-29
> **fasoulas said:**
> Which filesystem perform faster?

And if isn't nesessary to have access from windows what other options do i have?

It can be statistically proven that you've got mostly small files on your hard drive. ReiserFS is designed for handling small files better. I can say my hard disk is much quieter when accessing reiserfs compared to ext3.

---

### Post by esaym on 2006-10-29
> **fasoulas said:**
> Which filesystem perform faster?

And if isn't nesessary to have access from windows what other options do i have?
honestly they are all different.  In benchmarks some take longer to create 1000 directories and others take longer to delete 1000 directories.  As far as read and seek times, they are all very close.  As far as I go, I use ext2 because I enjoy vintage computing :p

---

### Post by fasoulas on 2006-10-29
JFS, ReiserFS XFS 

Comment these file systems ?

Speed.small files,big files e.t.c.

---

### Post by fasoulas on 2006-10-29
> **mahy said:**
> It can be statistically proven that you've got mostly small files on your hard drive. ReiserFS is designed for handling small files better. I can say my hard disk is much quieter when accessing reiserfs compared to ext3.

when you say small files what size is the limit?

---

### Post by mahy on 2006-10-29
> **fasoulas said:**
> when you say small files what size is the limit?

I think you take it too seriously. :D Dunno, maybe 1 MB, but that doesn't mean it can't handle big DVD images. As an ordinary user, you really don't have to bother, i don't either.

---

### Post by esaym on 2006-10-29
> **fasoulas said:**
> JFS, ReiserFS XFS 

Comment these file systems ?

Speed.small files,big files e.t.c.
The more you read the more you realize it doesn't matter :D

[http://www.google.com/search?hl=en&q=jfs+benchmark&btnG=Google+Search](http://www.google.com/search?hl=en&q=jfs+benchmark&btnG=Google+Search)

---

### Post by esaym on 2006-10-29
> **esaym said:**
> The more you read the more you realize it doesn't matter :D

[http://www.google.com/search?hl=en&q=jfs+benchmark&btnG=Google+Search](http://www.google.com/search?hl=en&q=jfs+benchmark&btnG=Google+Search)
also more good ones:

[http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)

[http://linuxgazette.net/122/piszcz.html](http://linuxgazette.net/122/piszcz.html)

---

### Post by furiousV on 2006-10-29
All that really matters is that the kernel can handle the filesystem well, and the filesystem has journalling.

---

