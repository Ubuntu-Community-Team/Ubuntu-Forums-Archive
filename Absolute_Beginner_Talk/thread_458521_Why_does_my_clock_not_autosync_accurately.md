---
title: "Why does my clock not autosync accurately?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by stevezygote on 2007-05-29
I am running Ubuntu 7.04 on a VMWare virtual drive hosted by Windows XP Home SP2. The hardware is a 2.2Ghz Celeron Processor with .5GIG RAM and a 64MEG Video Card. The HDD is a 82 GIG Maxtor with a C NTFS and a D FAT manufacturer's partition. 

The problem is....my clock in Ubuntu doesn't sync correctly.  In WIndows it's dead on. But every time I restart my Ubuntu system I have to change the clock. I've set sync to internet time servers and chosen a couple very close to me. There is none in my time zone though. Pacific.

---

### Post by dbbolton on 2007-05-29
do you have NTP support installed?

---

### Post by jhernandez1270 on 2007-09-04
check to see if your rcS file has UTC=no

under /etc/default
edit your rcS file and set UTC=no

---

