---
title: "Problem Partitioning From Ubuntu"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Ciansy on 2007-07-23
Hi,

I have a new PC that came with  Windows Vista pre-installed, and I'm trying to install Ubuntu 7.04 so that I can dual-boot it. I partitioned my HD from Vista after defragging without a problem, and I now have plenty of HD space set aside both for Ubuntu and for the swap partition. However, when I load the Ubuntu desktop from CD and select 'install', I can't create a partition from the free space available for both Ubuntu and the swap: whenever I create one or the other the installer informs me that the rest of the space is now 'unusable'. Please, can anyone help me out here?

Thanks.

---

### Post by sacherjj on 2007-07-23
I usually make the swap space first, towards the end of the free space, then try to make the Ubuntu partition.  While you are at it, do yourself a favor and make a separate /home partition.  It makes reinstalls and other things much easier.

---

### Post by asmoore82 on 2007-07-23
At first I found it strange that Ubuntu liked to use an Extended Partition and /dev/hda5 as swap...
but now I just like Ubuntu auto-partition stuff like it wants....

have you tried use largest free space and auto??

---

### Post by Ciansy on 2007-07-23
> **asmoore82 said:**
> have you tried use largest free space and auto??

I just tried that, it seems to be working out ok. Even making a very small swap space first didn't work, it render the (quite large) amount of free space left unusable. Gah! I hope the guided partitioning doesn't create any problems with the other OS.

Thanks for the advice!

---

### Post by xael on 2007-07-23
> **Ciansy said:**
> ... I hope the guided partitioning doesn't create any problems with the other OS...

Normally, there's no problem if Windo$$$ is installed. Ubuntu autodetects it and sets everything correctly. So,  go ahead and enjoy. :popcorn:

---

