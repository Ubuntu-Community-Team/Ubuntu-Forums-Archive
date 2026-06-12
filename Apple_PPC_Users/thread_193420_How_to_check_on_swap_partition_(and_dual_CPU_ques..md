---
title: "How to check on /swap partition (and dual CPU ques.)"
date: 2006-06-10
forum: Apple PPC Users
---

### Post by swartzfeger on 2006-06-10
All,

Kubuntu performance has been only so-so on my dual G5. First I did

cat /proc/cpuinfo

to ensure linux recognized both CPUs. It did an everything was ok.

Next question -- something's telling me that I don't have a swap partition... I don't know why, but I don't recall seeing it in my media file manager (and I'm in OS X right now).

Is there a quick/dirty way in the Konsole to see which /dev, if any, is designated as the swap drive?

Also, just because the system reports seeing 2 CPUs doesn't necessarily mean it's USING both, correct? ie, how can I tell I'm using a SMP kernel and not a single CPU kernel? (does that makes sense, or am I needlessly complicating things?)

Thanks!

---

### Post by tidris on 2006-06-10
To see partition info:
sudo fdisk -l

To see which kernel you have:
cat /proc/version

---

