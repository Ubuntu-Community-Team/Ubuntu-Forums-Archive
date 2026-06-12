---
title: "Is There A Limit?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by freakboysystem on 2007-05-12
Hi, Is there a limit to how much hard-drives and capacity Ubuntu can take, same with memory (ram).
I _DONT_ mean how much can my motherboard can take how much Ubuntu can take.

---

### Post by bernied on 2007-05-12
I believe this is limited by the kernel, and by the filesystem that you use. Also perhaps by your bios.
I don't think you need to even think about it until you have more than 4GB RAM and 2TB on a single filesystem.

Does this apply to you?

---

### Post by freakboysystem on 2007-05-12
Well, Im planning on upgrading from 2gb ram to 3gb, and upgrading my 160gb to 750gb. i cant seem to find that new 1tb drive.
another question for the future.
blu-ray hd dvd will it work?. ( that may be a stupid question becasue no ones probably ever tried it but ,yeh)
Thank You.

---

### Post by [S|G] on 2007-05-12
Non 64-bit systems can use up to 4gb of ram, while 64-bit systems can use up to 16 exabytes (16 billion gigabytes). That's mostly an architecture limitation. I'm not sure as to how much maximum RAM linux supports under 64bits, but it is at least 64gb.

As for disk space, ext3 running on x86 (non 64bit) can support partitions of up to 2tb and under 64bits it supports sizes of up to 32tb. Note that you might be able to use larger disks, divided on more than one partition.

---

