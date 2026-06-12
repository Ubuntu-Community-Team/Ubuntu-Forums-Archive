---
title: "No space left on device, Kernel compile"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by ann1 on 2007-10-12
Hi,
When I compile a new kernel, it fails at "make all", saying "No space left on device". I checked with df -h, and it says that /dev/sda3 has 3.8G and all is used up. I then checked with Disk Usage Analyzer and most of the space (51%) is taken by the new kernel at /usr/src and most of it is taken by drivers. Now, how to make space here.
Thanks,
Ansuya

---

### Post by cmnorton on 2007-10-12
Get the output from df.
Check the kernel targets from the build, and see if the targets are set to a small partition.

---

