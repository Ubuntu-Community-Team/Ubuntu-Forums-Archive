---
title: "Sporadic lags"
date: 2017-08-14
forum: Apple Hardware Users
---

### Post by matty29 on 2017-08-14
Hello guys,
I have got a Macbook Pro Early 2011 with Ubuntu 16.04 on it working since 1 year. I haven't problems with it except this: sometimes (once in a week) it starts lagging, then it disconnects and I'm forced to reboot. I would like to precise that it doesn't completly crash, it becomes very laggy and slow.
Ever heard anything similar to this? 
Thanks

---

### Post by TheFu on 2017-08-14
i don't think this is an apple-only issue.

Since loading 4.10 kernel on my 16.04 system (I loaded the HWE patches to fix a GPU issue, which has been fixed), I'm seeing lags (nearly lockup) when firefox memory and CPU use balloons every 3-5 minutes.  My system only has 4G of RAM, so when Firefox wants 9+G, there is an issue. This didn't happen on the 4.4 kernels.

So the first thing you should do is figure out which processes are using all the GPU and RAM and SWAP.  That is how I determined it was firefox and not some other system tool causing the problem for me. I don't have a solution, but at least I know what to look for.
```

top - 17:04:49 up 21:19,  3 users,  load average: 0.64, 0.65, 0.77
Tasks: 202 total,   3 running, 199 sleeping,   0 stopped,   0 zombie
%Cpu(s): 13.2 us,  2.1 sy,  0.0 ni, 84.4 id,  0.1 wa,  0.0 hi,  0.2 si,  0.0 st
KiB Mem :  3911140 total,   211024 free,  3434096 used,   266020 buff/cache
KiB Swap:  4300796 total,  3354468 free,   946328 used.   162896 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND    
26814 thefu     20   0 6660960 2.475g  44652 R  50.5 66.4 296:26.64 firefox
```

BTW, it just happened while I was making this post - about a 30 sec stop.

---

### Post by matty29 on 2017-08-16
I still have the kernel 4.4 and 4GB ram...I don't have the swap partition on the HD, but honestly I have never seen all the ram used. For example last time it happened while watching a video in 720p online with just only firefox opened. While I had the version 14.04, it never happened.

---

### Post by TheFu on 2017-08-17
Firefox will easily suck 4G of RAM. Easily.  My system has 4G of RAM and a 4.xG swap and FF is currently sucking over 8G of virtual RAM. 10 tabs are open - none with Flash/Video. I've removed those plugins. I'm looking into ways to limit the FF RAM use via a container so it can be limited to 2G or less.  

FF sucking RAM is my issue and I would be surprised if it  wasn't yours too.  FF is a hog.

---

### Post by matty29 on 2017-08-17
I shall check the ram amount when it will happen next time and make an attempt adding a swap partition. Thank you for your help, I would have never thought it could be firefox.

---

### Post by abtabt on 2017-08-18
> **matty29 said:**
> I shall check the ram amount when it will happen next time and make an attempt adding a swap partition. Thank you for your help, I would have never thought it could be firefox.
Install htop its more info than top and you can kill process easy etc run it as root

---

