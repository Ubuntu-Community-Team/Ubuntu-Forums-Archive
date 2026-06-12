---
title: "How to install Ubuntu 6.06_64 on multi-boot HD"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by satimis on 2006-07-25
Hi folks,

I have a HD running FC5_64.  The HD, which has 80G in capacity with half of it used, was partitioned with LVM with following config.

/boot not in VolGroup00, on /dev/sda1

/dev/sda2
# lvscan```

  ACTIVE            '/dev/VolGroup00/LogVol00' [9.75 GB] inherit
  ACTIVE            '/dev/VolGroup00/LogVol01' [11.72 GB] inherit
  ACTIVE            '/dev/VolGroup00/LogVol03' [1.00 GB] inherit
  ACTIVE            '/dev/VolGroup00/LogVol02' [5.00 GB] inherit
  ACTIVE            '/dev/VolGroup00/LogVol04' [5.00 GB] inherit
```

LogVol00 for / of FC5_64
LogVol01 for /home of FC5_64
LogVol03 swap

LogVol02 ext3 is for / of Ubuntu 6.06_64
LogVol04 ext3 is for /home of Ubuntu 6.06_64

I selected "manually edit partition table" to proceed but can't netvigate installing / to LogVol02 and /home to LogVol04.  Each time it asked to reformat HD.

Please advise how to proceed.  TIA

B.R.
satimis

---

