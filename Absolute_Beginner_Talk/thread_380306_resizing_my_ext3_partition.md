---
title: "resizing my ext3 partition"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by bluezapper on 2007-03-09
Hi All,

I have attached a screenshot of my Gparted disk window which shows my partitions.

As you can see I have only 1.4 GB of space left on my /dev/hda3 partition and I am desperate to increase its size and I still have unallocated space of around 4.43 Gb which I want to add to my /dev/hda3 partition.

I am unable to do it as /dev/hda3 partition is locked as you can see in the screenshot. Please help me in solving this problems before I run out of space.

I am a noob to linux and my partition table looks crappy,sorry.


waiting for your replies,

thanks

bluezapper.

---

### Post by taurus on 2007-03-09
You cannot resize your partition while it is being used.  Therefore, you need to boot your machine with the LiveCD before you can resize it.

Meanwhile, run this command from a terminal to free up more space.

```
aptitude clean
```

---

