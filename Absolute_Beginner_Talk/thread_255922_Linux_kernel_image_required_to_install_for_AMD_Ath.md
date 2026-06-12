---
title: "Linux kernel image required to install for AMD Athlon(TM) xp 2000+"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by kurian on 2006-09-12
hi, 

 Iam new to linux .I run kubuntu in my pc.........

 I want to know which linux kernel image should i install for my PC

 my processor is : AMD athlon(TM) xp 2000+

 with 1.66GHz.


 kindly post a quick reply along with how to install the required kernel image............

---

### Post by risbac on 2006-09-12
For AMD processors, you usually have to use the K7 versions.
So something like "linux-image-2.6.15-26-k7"

---

### Post by kurian on 2006-09-12
hi, thanks for the reply.......

But i do have a doubt whats the real advantage of changing linuxkernel from the default 386 to the one listed above.........

will there be any performance improvement on a large scale???

---

### Post by halfvolle melk on 2006-09-12
There might be for specific tasks. I'd say install it. You can always boot into the old kernel if it doesn't work out for you. Also see:
[http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

---

### Post by az on 2006-09-12
Install the "linux-k7" package and not just the linux-image-xxx package.

That installs the restricted modules too, and you may or may not need them.

---

### Post by kurian on 2006-09-17
could you please give me the code for installing the kernel for amd athlon xp 2000+

---

### Post by Anduu on 2006-09-17
sudo apt-get install linux-k7

---

