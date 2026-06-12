---
title: "Installing Ubuntu, some questions"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by woldy on 2008-02-08
Sorry if these questions have been answered elsewhere but my searches yielded no results.
So after trying to resize my partition for weeks with various versions of GParted, I finally found System Rescue CD which worked wonderfully for me,  I resized my main partition which has XP on it so I have 10GB of Unallocated space. Should I create a new partition before trying to install Ubuntu, if so which filing system? or will it do it for me?  I have already tried to install Ubuntu but my screen turns off after a few seconds so I am downloading the alternate version. is there anything difficult about installing with the alternate version? sorry about the long post, thanks for the help in advance.

---

### Post by forestpixie on 2008-02-08
I'd make an ext3 partition for root / and then an extended partition and put a swap partition inside that

If you use hibernate make swap same as ram if not 512Mb or 1Gb - I have 1Gb ram and very rarely use swap

use the remaining space for your root partition

---

### Post by jan quark on 2008-02-08
here is a good guide explaining the steps during the alternate install

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by woldy on 2008-02-08
One more thing I want the 64 bit option with my Core 2 Duo right? or should I just use the x86? Also I downloaded an md5sum(I think thats what it is) checker thing, but what do I compare the number it gives me to? to make sure it's not corrupt.

---

### Post by forestpixie on 2008-02-08
ebf7ad055bc39634065daa10de980d7e *ubuntu-7.10-alternate-amd64.iso
9a4ae3cfd68911a861d094ec834c9b48 *ubuntu-7.10-alternate-i386.iso
61c87943a92bc7bf519da4e2555d6e86 *ubuntu-7.10-desktop-amd64.iso
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso
43ff753b260729b12c7d21d3a6db8c73 *ubuntu-7.10-server-amd64.iso
7d88cd87df509a740d9f47b9bbf1375e *ubuntu-7.10-server-i386.iso
5308a79f5e652edba5be84644ee14b09 *ubuntu-7.10-server-sparc.iso

---

### Post by forrestcupp on 2008-02-08
You can use either the x86 version or the 64-bit version.  If you're insistent about using 4 GB of RAM or more, you can use the 64-bit.  I personally tried the 64-bit and went back to x86 because certain things aren't working well.   There is no 64-bit version of Flash, and it is a major pain to get it working.

---

### Post by jan quark on 2008-02-08
you can check if your cpu supports 64 bit with this terminal command
```

sudo lshw -C cpu
```

---

### Post by jan quark on 2008-02-08
> There is no 64-bit version of Flash, and it is a major pain to get it working. 

this is not correct, I have 64 bit and flash working, the installation is easy and the problems are fixed

see this thread
[http://ubuntuforums.org/showthread.php?t=689637](http://ubuntuforums.org/showthread.php?t=689637)

---

### Post by nodegamra on 2008-02-08
I am Using the 64 bit version of Ubuntu and it works fine. There is a script that installs flash without any problems in less than a minute. Other than that it works great!

Here is the post :
[http://ubuntuforums.org/showthread.php?t=476924&highlight=64bit+flash](http://ubuntuforums.org/showthread.php?t=476924&highlight=64bit+flash)

---

