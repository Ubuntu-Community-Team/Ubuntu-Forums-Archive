---
title: "How do I mount PC-BSD file system?"
date: 2011-04-10
forum: Any Other OS
---

### Post by pcbsdfhte on 2011-04-10
I use Ubuntu 10.10 and PC-BSD(FreeBSD) 8.2. But I can't mount all FreeBSD file system. 

I tried
sudo mkdir /mnt/pcbsd
sudo mount -t ufs -r -o ufstype=ufs2 /dev/sda3 /mnt/pcbsd

The UFS mounted, but not all slices(partitions). I installed PC-BSD by "Auto Partition", but I think the slices are composed of /, SWAP, /var and /usr. 

But the /mnt/pcbsd directory have /mnt/pcbsd/var and /mnt/pcbsd/usr but these directories don't have any file or directory.

---

