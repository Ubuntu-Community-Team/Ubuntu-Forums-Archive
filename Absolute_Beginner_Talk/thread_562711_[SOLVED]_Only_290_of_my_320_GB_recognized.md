---
title: "[SOLVED] Only 290 of my 320 GB recognized"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by vasocreta on 2007-09-29
So, I am beginning to love this Ubuntu thing! I wouldn't even think of turning back to windows now, even though I still have to get my Cannon MP530 to work correctly and my graphics card to run optimally. But my question for today is:
Why does Ubuntu Feisty Fawn only recognize 290GB of my 320GB hard drive?

I am not using a dual boot machine, so Linux is all that is on my HD.

I am not even sure how to begin diagnosing the issue.

Any thoughts?

Thanks.

---

### Post by dcstar on 2007-09-29
> **vasocreta said:**
> So, I am beginning to love this Ubuntu thing! I wouldn't even think of turning back to windows now, even though I still have to get my Cannon MP530 to work correctly and my graphics card to run optimally. But my question for today is:
Why does Ubuntu Feisty Fawn only recognize 290GB of my 320GB hard drive?

I am not using a dual boot machine, so Linux is all that is on my HD.

I am not even sure how to begin diagnosing the issue.

Any thoughts?

Thanks.

Hard drives sizes are specified two ways - per 1,000 bytes or in multiples of 1,024 bytes.

The former is used by HD manufacturers to inflate the apparent capacity of their products, the latter is used by everyone else to match (almost) all other computer measurements, don't worry about the "issue", there probably is no difference.

My "80GB" drive is reported as 74.53Gib, but it is still an "80Gb" drive.

---

### Post by Bothered on 2007-09-29
Could you enter the following in a terminal and post the results:

```
sudo fdisk -l
```

One possible reason is that you have a 320 GB drive, and your reading the size of the drive in ubuntu in GiB - 1GiB = 1.07GB (see [here]("http://en.wikipedia.org/wiki/GiB") for explanation of GiB).

---

### Post by PeterF on 2007-09-29
To see how your harddisk is partitioned you can use 
```
sudo fdisk -l

```
Part of your harddisk will be reserved for swap.

---

### Post by Lord Illidan on 2007-09-29
Also 5% of the filesystem is usually set aside for root. (So that normal users cannot really fill up the drive..and root user can clean up).

---

### Post by rfurman24 on 2007-09-29
> **dcstar said:**
> Hard drives sizes are specified two ways - per 1,000 bytes or in multiples of 1,024 bytes.

The former is used by HD manufacturers to inflate the apparent capacity of their products, the latter is used by everyone else to match (almost) all other computer measurements, don't worry about the "issue", there probably is no difference.

My "80GB" drive is reported as 74.53Gib, but it is still an "80Gb" drive.

This is correct. My 500gb shows around 450gb, I can not remember the exact number. I believe the difference is gigabytes vs gigabits.

---

### Post by vasocreta on 2007-09-29
These are the results from fdisk -l

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       38536   309540388+  83  Linux
/dev/hda2           38537       38913     3028252+   5  Extended
/dev/hda5           38537       38913     3028221   82  Linux swap / Solaris

I am not good at reading this stuff yet, but I think that I can at least see that my full drive capacity is in fact recognized, but what I see as the filesystem capacity has to do with how things are partitioned.

Thanks, all. I am still not used to the very libertarian approach that Linux offers to managing my computer. I am used to the socialist approach of Windows.

I am happy to say that I no longer subscribe to the MS agenda!
Y'all rock!

---

