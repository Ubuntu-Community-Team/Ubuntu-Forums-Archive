---
title: "How to Boot from an external firewire cd unit?"
date: 2005-09-29
forum: Apple PPC Users
---

### Post by RTemplar on 2005-09-29
Hi there, I'm absoulty an newbie...

I have a iBook 500 Dual USB, with an internal combo dirve dead... So, I bought an external carry disk (I have read that my iBook only boots from firewire, not from usb...) and attached a cd-rw pc unit in it... This work well, so I backed up my data and decided to reinstall, and partition my hd in three (Unbuntu 5.04, OS X 10.3, and AIX -I don't know if I'm going to be able to install AIX, but leaved a partition for it just in case...-)...

Now... I cannot find the way to boot from the install, or live cd, from the external CD-rw drive... 

I followed the procedure to boot from Open Firmware, but only got a: "can't Open error" from the command: 0> boot hd:X,yaboot (I have previously copied the 4 files to root directory...)

df -k (output):
/dev/disk0s6              5505016 3592440  1857528    66%    /
/dev/disk0s3             22511360   28364 22482996     0%    /Volumes/Unbuntu (5.04)
/dev/disk0s4              1024000   16048  1007952     2%    /Volumes/AIX
/dev/disk1s1s2             641940  641940        0   100%    /Volumes/Ubuntu_PowerPC_hoary

How can I address to boot from the FireWire External CD drive?

Can anyone point me in the right direction?

Thanks, r

---

### Post by RTemplar on 2005-10-07
Anyone? No one can point me in the right direction?... r

---

