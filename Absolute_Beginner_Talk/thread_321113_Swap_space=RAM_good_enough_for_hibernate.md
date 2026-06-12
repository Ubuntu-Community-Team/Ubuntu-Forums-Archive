---
title: "Swap space=RAM: good enough for hibernate?"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-12-18
Hi,

I plan on using suspend2 (kernel patch) to hibernate my laptop. The laptop has 1Gb of RAM and for now my swap partition is set to 1Gb as well. I was wondering if this swap space is enough for hibernation on my system. I understand that for hibernation I should at least have a swap space = RAM to allow all the RAM to be saved on the disk. However I guess that when you use all the RAM already there is a good chance you're also using some swap space before entering hibernation.....so having swap space=RAM shouldn't be enough. Or does the hibernation compress data that was in RAM????

It's probably safer to go with a swap of 2Gb but I don't like resizing partitions when I have data on them since for now I don't have any backup solution. So do you think that 1Gb swap for 1Gb RAM is enough for hibernation?

Thanks

---

### Post by bodhi.zazen on 2006-12-18
Memory is different with Linux and in particular Windows.

With 1 Gb ram it is unlikely you ever use your swap at all.

In a terminal you can type```
free
```to see your memory use.

At any rate, 1 Gb swap should be just fine. In a pinch you could likely do with less ....

---

