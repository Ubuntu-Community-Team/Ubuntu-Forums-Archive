---
title: "Ubuntu boot issue"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by harry rao on 2008-04-02
hi,

this is what is appearing when i attempt to boot into ubuntu 7.10:

* Reading files needed to boot                  [ok]

* Preparing restricted drivers                     [ok]

Setting System clock

*starting basic networking                         [ok]

*starting kernel event manager                 [ok]

udevd - event [3822]: run_program '/sbin/modprobe' abnormal exit  [ok]
setting up system clock

* loading manual kernel modules...
* loading manual drivers... 


Then the screen remains at this position and doesn't progress, i've read through as many posts as i can and there seemed to be no issue with the same error code.

help would be much appreciated.

---

### Post by kellemes on 2008-04-02
You have an external drive hooked on?
This is a first install of Ubuntu 7.10?

As I understand it this is a [bug in the kernel]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154591"), there are ways to handle this but you need to manually compile a new kernel, not sure if this is what you want.

An easier way of handling this is to install Hardy as the kernel provided has this issue fixed. (as far as I know)
[http://www.ubuntu.com/testing/hardy/beta]("http://www.ubuntu.com/testing/hardy/beta")

---

### Post by harry rao on 2008-04-02
no, it's been installed for about a month.
it's running from my internal hard drive
it's been working perfectly fine since then, this is a completely new error.

---

### Post by hyper_ch on 2008-04-02
do you have an older kernel in the boot menu to select? Does it work with that?

---

### Post by harry rao on 2008-04-02
no, i only have 7.10 gutsy gibbon

---

### Post by sayakb on 2008-04-02
appears as if the kernel broke down.. Can you boot into recovery mode. If so, then try re-installing the kernel:
```
sudo apt-get remove linux-generic
sudo apt-get install linux-generic
```

---

### Post by harry rao on 2008-04-02
thank you, let me try it out and get back to you once i've tried your solution 'LinuxIsInnovation'.

---

### Post by harry rao on 2008-04-02
alright, it worked only because i pressed "alt+F2" - now i'm even more confused, even though i'm on ubuntu i have no idea how?

---

### Post by Kanji_Man on 2008-04-06
For what it is worth I recently encountered the same problem as the original poster when applying the 2.6.24-15 kernel update on Hardy Beta. On another system I attempted a fresh install of Hardy Beta and when I apply all the updates (including the 2.6.24-15 kernel) I once again (reliably, predictably, repeatedly) am presented with this problem.

Following the advice of this thread I was able to boot the older kernel from the Grub menu, I reinstalled the package linux-generic (or linux-rt on another system) and all the systems boot fine.  I have not encountered this problem when upgrading previous kernels.

---

### Post by silverpig on 2008-04-07
I too have this problem.

2.6.24-15-generic hangs
2.6.24-14-generic hangs
2.6.24-12-generic works

I did the apt-get remove linux-generic and then re-installed it and it didn't work.

---

