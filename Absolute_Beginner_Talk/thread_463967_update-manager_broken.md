---
title: "update-manager broken"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by gregcha117 on 2007-06-04
this is getting frustrating, I tryed replacing my sources.list with a newly generated one and when i run sudo apt-get update it seems to get everything fine until the end when i get this error

'E:Read error - read (21 Is a directory), E:The package lists or status file could not be parsed or opened.'

i cant install anything via apt and its beginning to get quite frustrating I'd love for some help to fix this problem.

---

### Post by loathsome on 2007-06-04
Open [COLOR="DarkSlateGray"]/etc/apt/apt.conf[/COLOR] and tell us what it says on this line:
**APT::Cache-Limit xxxxxxxx;**
Try setting it to :
**APT::Cache-Limit 20000000; **

---

### Post by gregcha117 on 2007-06-04
i dont seem to have one instead i have /etc/apt/apt.conf.d/ with a few files inside and nowhere in any of them do i see a reference to cache-limit

---

