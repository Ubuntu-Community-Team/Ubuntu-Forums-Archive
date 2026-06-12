---
title: "gptsync packages for MBR sync update intel macs"
date: 2009-04-06
forum: Apple Hardware Users
---

### Post by pxwpxw on 2009-04-06
Checking or updating the MBR/GPT tables sync can be done from ubuntu or debian linux live cd. There is a Ubuntu refit package with gptsync for i386, not for amd64.

The refit gptsync and showpart utiltiy for i386 and amd64 are downloadable from debian mirrors - package name gptsync, very small so copies are attached.
```

http://packages.debian.org/squeeze/gptsync

Architecture  	Package Size/Installed Size
amd64-----------20.5 kB/72 kB 
i386------------19.7 kB/68 kB  

sudo dpkg -x gptsync_0.12-2_amd64.deb .
sudo ./sbin/gptsync /dev/sda


(or for i386 gptsync_0.12-2_i386.deb )

(use dpkg -i gptsync_0.12-2_amd64.deb to install permanetly in /sbin and /usr with docs and man pages)

```
That enables sync/uopdate the MBR, or show MBR/GPT partitions from linux.
Same as the refit Partition Tool  and Partiton Inspector.

---

### Post by george-harrison on 2009-04-06
Thanks for useful information.

---

