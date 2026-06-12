---
title: "Can install Freshclam"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by mscoxoh on 2007-04-06
I've determined that freshclam is not installed on my system, so I did this:

> sudo apt-get install clamav-freshclam

and get this error:

The following packages have unmet dependencies:
  clamav-freshclam: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
E: Broken packages

Can someone translate and tell me how to fix? Looks like I need to update... libraries? libc6? Any help appreciated

.m.

---

### Post by tbroderick on 2007-04-06
Are you running  Edgy? Did you sudo apt-get update first?

---

### Post by mscoxoh on 2007-04-06
> Are you running Edgy? Did you sudo apt-get update first?

Thanks for the reply. I'm running 6.06 LTS. Yes I did the apt-get update.

Michael

---

