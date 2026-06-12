---
title: "Primary partion vs extended"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2006-09-04
Hi,
  I have a tri-boot system.  When I went in to make my partitions using gparted, I did the following:

- primary ntfs
- primary ext3 mandy
- primary fat32
- extended partiton
..|_ primary ext3 ubuntu
..|_ primary linux swap

My question is, does installing ubuntu and my swap mess with my mounts, do I have to mount them in a special way since it is not a primary partition but an extended one?  I'm just curious about this for future reference.  I would imagine if you mount them correctly, the type of partition wouldn't matter, but I'm still learning.  Thank you!

---

### Post by bodhi.zazen on 2006-09-04
Short answer, no it does not matter.

---

