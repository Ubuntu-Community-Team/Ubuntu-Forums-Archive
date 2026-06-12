---
title: "Advice on partitions"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2006-08-20
I'm using GParted to resize my NTFS partition (hda1) and redo my entire hda2 (extended) partition. Here's my plan:

38.09GB NTFS, freshly defragmented (that's all I could spare with the data already on the drive), resized from 50 GB

17.80GB Extended:
- 5.91GB ext32 for every directory except /home
- 2.88GB ext32 for /home
- 1GB swap

- 8.03 GB (remaining) for fat32 shared space

Anyone have any suggestions for my layout?

---

### Post by anaconda on 2006-08-20
5,91GB for "root" / partition is not enough.
2,88GB for home is also not enough
In this case 8GB for file sharing is too much.

Here is what I would do:
17,80GB extended partition divided to:
16,8GB "root" partition including /home
1GB for swap
and then use [http://www.fs-driver.org/](http://www.fs-driver.org/) in windows to do file sharing from your linux-partition. Eg. your linux partition is the file sharing partition.

Or if you want to have a separate /home, then
10GB "root" partition
and 6,8GB /home
1GB swap

Oh. and I when I said that 5,91GB for root partition is too little.. I know that some people have a working ubuntu in 6GB (or smaller) hard-disk, But 6GB can waaay too easily become full if you install any bigger programs

---

### Post by rowanparker on 2006-08-20
I wouldn't separate /home but that's good if your using it in multiple distros.
And a bigger root might do good.
Apart from that it is alright.

Edit: Damn, anaconda beat me to it.

---

