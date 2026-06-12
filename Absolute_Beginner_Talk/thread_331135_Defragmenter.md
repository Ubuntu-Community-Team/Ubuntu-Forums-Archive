---
title: "Defragmenter"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by fredster001 on 2007-01-04
Hi, 

In windows there is a defragmenter, however i am yet to find one in ubuntu.
Is there one or is it not neccessary??


Thanks

fredster001

---

### Post by CroEragon on 2007-01-04
I think (not sure) that ext3 is designed that it doesn't get fragmented easily. So i think you need no defragmentation software for Linux. Idont know.

---

### Post by xyz on 2007-01-04
Hi,
Most people say it's not necessary and it's not.
Check this out if you like:
[Defrag any filesystem]("http://www.ubuntuforums.org/showthread.php?t=133428&highlight=defrag")

---

### Post by xiaoxin on 2007-01-04
There is no deframentation program in Linux because the ext3 filesystem is self sufficient

---

### Post by insane_alien on 2007-01-04
ext3 will defragment itself on the fly. which means its doing it every time you create or delete a file. with linux, you don't need to worry about ANYTHING

---

### Post by ajgreeny on 2007-01-04
Just to put yopur mind at rest, after 30 bootups (unless you change things yourself) your root file system will do a filecheck at boot time (fsck) and assuming all is OK will show on the text that's showing the percentage of non-contiguous files, mine has never got higher than 2.9%.

---

### Post by pseudonym on 2007-01-04
If you use xfs there is a defrag utility in the xfsdump program. Because xfs is  often used for storing large files (like movie-length .mpegs and .avis), which fragment very easily, it can be useful to defrag them if you need to store them on your hard drive for a while.

But for the more common journalling files systems like ext3 and reiser, the way data is written to them means fragmentation will only occur if the partition gets 95% full or more. And these filesystems effectively prevent that from happening by 'reserving' about 4-5% of the partition.

There are a million links out there which explain this in more depth, though.

---

### Post by mykalreborn on 2007-01-04
you don't need to defragment a linux system. it's designed that way.:D
there was a tutorial somewhere explaining why... hmmm. let me see...

yup here it is:[link]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")

hope it answers your question

---

### Post by CroEragon on 2007-01-04
You can find explanation [here.]("http://blog.mypapit.net/2006/09/why-you-dont-have-to-defrag-linux-like-windows.html")

---

### Post by Sweet Spot on 2007-01-19
OK, I think that everybody understands that Linux file systems don't need to be defragmented, and that's just simply wonderful. I'm overjoyed. Honestly. 

But there's only been a couple of people commenting on why they'd need a defrag tool for something other than defraging said file systems. 

How about since Linux (Ubuntu for me in particular since it's what I use) is so UMS friendly, people whom have an Mp3 player such as say, an iRiver, iAudio, and even an iPod running ROCKbox (I have the IHP 120 and an iPod 5g running RB) might not want to have to boot into Windows just to defrag their FAT 32 Mp3 players file system ?

It's just one more reason why I can't completely get Windows off of my HD.

---

### Post by mykalreborn on 2007-01-20
here is a website with some software to manage your ipod:[http://gnomefiles.org/search.php?search=](http://gnomefiles.org/search.php?search=). i don't know if they have a defragmenter option though.

---

