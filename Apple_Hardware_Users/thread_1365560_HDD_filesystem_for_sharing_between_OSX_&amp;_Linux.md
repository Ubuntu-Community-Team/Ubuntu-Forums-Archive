---
title: "HDD filesystem for sharing between OSX &amp; Linux"
date: 2009-12-27
forum: Apple Hardware Users
---

### Post by ssalman on 2009-12-27
Hi, I just got myself an external hard drive for backing up files from two different laptops, Ubuntu 9.10 and OSX 10.4 laptops. Some of the files can be rather large video files (as large as 13GB in size) and I would like to back up and access these files from both machines, is there a file system that I can format my new drive with so that I can access it from both laptops through USB? 

Thanks.

---

### Post by tom4everitt on 2009-12-27
Okay, so you have a couple of options, each with its own pros and cons:

fat32
This file system works flawlessly with all operative system, but it doesn't support bigger files than 4GB.

hfsplus
Supports big files, works well in os x. In linux it usually works alright, but if you remove the hard drive without unmounting it first, you will only be able to mount it read only in linux. To fix this you just need to mount it and unmount it in os x. 

ext2
supports big files, works well with linux, but requires the installation of [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/) to work in os x. I'm not sure how well this works, but you could try. 

ntfs
pretty much the same situation as for ext2, but you need to install this instead: [http://code.google.com/p/macfuse/](http://code.google.com/p/macfuse/)



My own opinion:
Use fat if your files are smaller than 4gb. If there not:
 --If you use os x a lot, use hfsplus
 --If you use os x only occasionally, use ext2 or ntfs

Hope it helps, its a bit of a mess...

---

### Post by ssalman on 2009-12-27
Thanks tom4everitt!

I spent some time today googling and reading online and I think you summarized it well. I was going to wait until I hear back from this thread, but I was leaning toward an NTFS FS. Thanks for the very well put summary and especially the links it helped me a lot, now I'm trying NTFS to see how well it works on OSX. Thanks again.

---

### Post by amd-64 on 2009-12-28
I use hfsplus to share virtual machines on a dual boot (OSX and 9.10). The files grow to 10Gb+ and I had no problems with it. 

It is unfortunate how all modern filesystems cannot be used for sharing.

---

