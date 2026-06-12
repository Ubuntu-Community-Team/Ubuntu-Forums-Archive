---
title: "Is it normal..."
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-08-12
to feel Ubuntu slower than XP? I remember a lot of people having said that Ubuntu (and most distros in general) was more stable, more safe and more fast than Windows XP. Well i have some problems with the last statement. Xmms, Amsn, Firefox, Azureus, all load faster in Windows. Firefox is what gives more problems, sometimes when i load a page with some flash embedded in it and then close it, it does not free the memory. I need to restart firefox to reach the normal memory usage.

Perhaps it has to be with the video drivers. I have and onboard SIS graphic video card. AFAIK, there is no available driver for this chipset to get 3d rendering under linux. 

Feedback would be appreciated

Thanks in advance

---

### Post by Arthur Archnix on 2007-08-12
Linux uses memory different than XP. From the command line do:
```
arthur@archnix:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1003        988         14          0          4        631
-/+ buffers/cache:        352        650
Swap:          486         33        453

```
Not sure if the formatting will come through, but you can see that 988MB is used, but 631 of that is cached. Actual used memory is 352. If I close Firefox right now it will stay in memory, so that it opens faster the next time I need it.

---

### Post by bren on 2007-08-12
ubuntu is about twice as fast as xp for me ....

(partly because norton cripples xp)

bren

---

### Post by syn` on 2007-08-12
I'm dual booting, and man, do I notice a performance jump from Ubuntu => XP. Ubuntu runs generally everything faster for me. Thank lord.

---

### Post by skymera on 2007-08-12
> **Arthur Archnix said:**
> Linux uses memory different than XP. From the command line do:
```
arthur@archnix:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1003        988         14          0          4        631
-/+ buffers/cache:        352        650
Swap:          486         33        453

```
Not sure if the formatting will come through, but you can see that 988MB is used, but 631 of that is cached. Actual used memory is 352. If I close Firefox right now it will stay in memory, so that it opens faster the next time I need it.

thats useless.
it said 906mb was sued
and 96mb free?

yet system monitor said only 200mb used
no swap used

---

### Post by Jeremy23 on 2007-08-12
You are correct on Ubuntu using more memory that XP. But that's not to say it's a resource hog.

What Linux tends to do is keep everything in memory, rather that writing it out to swap. It prefers to *actually use* your memory. Windows likes to swap everything out, to keep your memory free. But what's the point of that? You can really feel the difference when running a program like, say, VMware on both Windows and Linux.

When running a VM on my Windows desktop, about the only thing you can do with your system is use the VM, because once you try and multitask, the system grinds to a halt. With the same computer, running the same VM on Ubuntu, I can run a VM, maybe play a little Urban Terror, check my email, no slowdowns.

So, it may seem Ubuntu is using more memory. But have a look at your swap space. On a system with 512 megs of RAM, I can be using 500MB of it, and still only be using about 20MB of swap. Windows users probably faint when they read that, but in reality, it equates to a much faster system. Windows generally uses 200-300MB of swap at a minimum.

---

### Post by Arthur Archnix on 2007-08-12
Things are useful to those that know their uses. 

This page [here]("http://www.bellevuelinux.org/free.html") might help you decide if it has any uses for you, alternatively, you can try 
```
cat /proc/meminfo
```

None of this has anything to do with your speedy firefox questions, but one of the mistakes I made when moving from Windows to Linux was to bring my ideas about memory and its uses with me. It turns out those ideas were useless.

Best,

Oh and well said Jeremy. I seem to recall reading that Vista has moved over to this sort of memory management.

---

### Post by ferpadro on 2007-08-12
Well, Windows XP does run faster than linux on my machine, but thats maybe im not using any type of antivirus (I dont have the level of paranoia other users seem to have). Anyways, here is the output of /proc/meminfo:

fernando@Athena:~/Desktop$ cat /proc/meminfo 
MemTotal:      1003312 kB
MemFree:        445948 kB
Buffers:         16896 kB
Cached:         415100 kB
SwapCached:          0 kB
Active:         284580 kB
Inactive:       243468 kB
HighTotal:       98288 kB
HighFree:          224 kB
LowTotal:       905024 kB
LowFree:        445724 kB
SwapTotal:     1277128 kB
SwapFree:      1277128 kB
Dirty:            4572 kB
Writeback:           0 kB
AnonPages:       96092 kB
Mapped:          49976 kB
Slab:            20848 kB
SReclaimable:    11120 kB
SUnreclaim:       9728 kB
PageTables:       1464 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   1778784 kB
Committed_AS:   381256 kB
VmallocTotal:   114680 kB
VmallocUsed:      4180 kB
VmallocChunk:   110412 kB

Can someone translate this for me?

---

