---
title: "Resolution problems"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by mguthriejr on 2008-02-26
Hi im running a compaq presario f756 
with an AMD turion 64 x2 processor with Ubuntu 32 bit
and an nvidia graphics card i am using the restricted driver but i still cant get more than
800X600.
I initially did a 64 bit install and i got the resolution to work somehow but when i reinstalled with 32 bit(because of wifi problems) i cant get it to work and i have no ideas what to do....
any help would be appreciated

---

### Post by pedro_orange on 2008-02-26
Simplest thing to do is just reconfigure your xserver using:

```

sudo dpkg-reconfigure xserver-xorg

```

Follow the instructions, and select resolutions appropriate to your monitor.

---

