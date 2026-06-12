---
title: "Other partition are not shown in Ubuntu"
date: 2012-09-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by stevenbb on 2012-09-05
I installed Ubuntu 12.04 and it works perfectly, however Yesterday, after I restarted my laptop, in Ubuntu I can only see the system partition. other partition had disappeared. 

I stucked in this problem once and I had to reinstall Ubuntu but can you tell me what's wrong here? how can i solve this problem.

---

### Post by oldfred on 2012-09-05
Welcome to the forums.

Where is it that you do not see the other partitions? How did you mount them?

Are they in the left panel of Nautilus? If mounted from that they will not still be mounted when you reboot. You have to add to fstab to permanently mount them.

Post these:

sudo fdisk -lu

sudo parted /dev/sda unit s print

---

### Post by stevenbb on 2012-09-06
thanks. I've solved my problem.

It is just simple to change my view setting in home => other partitions appear! ^^!
I found myself so chicken :))

---

