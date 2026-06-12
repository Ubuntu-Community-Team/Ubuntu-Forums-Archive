---
title: "Dual Boot Edgy PPC"
date: 2007-01-23
forum: Apple PPC Users
---

### Post by youthforlinux on 2007-01-23
I'm still convincing my friend to try ubuntu

ive repartitioned and resized my HD tons of times but that was on x86

my friend Really doesnt want to lose his OSX Partition
ive read in other posts that the best way to go is to use parted.
but will gparted work?

---

### Post by ssam on 2007-01-23
gparted is just a GUI on top of parted, so it should work just as well.

it is often recommended to turn journalling off on hfsplus partitions that you work with on linux.

make sure you have a back up. even if the software is a perfect, a power cut while resizing a partition would cause data loss.

---

