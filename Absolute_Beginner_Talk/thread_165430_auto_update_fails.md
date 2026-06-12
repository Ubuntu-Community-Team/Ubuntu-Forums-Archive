---
title: "auto update fails"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by lyleogle on 2006-04-24
I have installed 5.10 on a HP PII-450, I also installed it on a Dell PII-266 at the house.  House install went good runs great.  Here at work I cannot successfully run updates and xmit data to the Ubuntu device database.

Auto updates never completes.  When I run apt-get update in a terminal window it never completes either.  The file it is trying to read is null, 0 bytes. The path is var/lib/apt/list where the file is called lock.

Any help

Regards,

Lyle

---

### Post by lyleogle on 2006-04-25
UPDATE:

I reinstalled of course that did not help.  I tried the manual update with no success either.  I fired up synaptic and tried there, it failed also.  It could not resovle the addresses. I dug around and found we needed to set the "proxy Servers" again.  Once this was done it runs fine.

Can we consolidate the amount of redundant network settings among the various apps?

Regards,

A learning experience for sure.

---

