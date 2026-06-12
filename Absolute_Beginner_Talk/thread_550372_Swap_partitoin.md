---
title: "Swap partitoin"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Whgresiak on 2007-09-13
I am installing 7.04 right now. After selecting partitions I used one as the root folder and then used the other as a home. I asked if I really wanted to continue without a swap file. So I went back and couldnt figure out how to do it, so i went on. So my questions are:

1. How do you set up a swap file?
2. Is not having one bad? if it is will I need to reinstall?

---

### Post by misfitpierce on 2007-09-13
Technically they say you should have at least 512MB.... I myself use around a gig of HD for swap. Up to you tho not really needed but good to have.

---

### Post by diatribe on 2007-09-13
if you have a gb+ ram you should be ok with no swap partition

---

### Post by Whgresiak on 2007-09-13
Yeah I have a Gig. Should be okay then? Great.. really don't wanna go through all that again ;)

---

### Post by diatribe on 2007-09-13
a swap partition is the same concept as the paging file in windows, it just swaps programs from ram to space on your hard drive.  unless you are using most of your ram, you wont really need to swap out.  with a gb you should be fine unless you run vm's or ram-intensive software

---

### Post by Whgresiak on 2007-09-13
> **diatribe said:**
> a swap partition is the same concept as the paging file in windows, it just swaps programs from ram to space on your hard drive.  unless you are using most of your ram, you wont really need to swap out.  with a gb you should be fine unless you run vm's or ram-intensive software

Nope. Thanks Guys :D

---

### Post by zgornel on 2007-09-13
> **diatribe said:**
> a swap partition is the same concept as the paging file in windows, it just swaps programs from ram to space on your hard drive.  unless you are using most of your ram, you wont really need to swap out.  with a gb you should be fine unless you run vm's or ram-intensive software
Highly unrecommended. Use a swap file or swap partition. Usually, programs that store data in ram clean it at the end of their execution but if there is a memory leak you will experience crashes and degraded performance. Furthermore, you won't be able to use the hibernate feature. To create a 1GB swapfile and enable it:
```
sudo dd if=/dev/zero of=/swapfile bs=1024 count=1024
```
```
sudo mkswap /swapfile 1024
```
```
sudo swapon -a
```

---

