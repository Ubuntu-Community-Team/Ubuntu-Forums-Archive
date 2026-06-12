---
title: "Memory"
date: 2005-09-14
forum: Absolute Beginner Talk
---

### Post by LucoB on 2005-09-14
Hi 

I have just installed Ubuntu and realised that my memory useage is 253,476KB and about 3,000KB free, the swap file isnt being used either. When i installed Ubuntu i set up a swap partion. 

Also when i select to put deivce icons on the desktop the swap partion is there but unmounted. Any ideas how i mount this and assign it as a swap file forever?

ALso a bit unrelated, how do you uninstall netbeans? downloaded from the sun site. 

Thanks

---

### Post by xequence on 2005-09-14
Ubuntuguide.org tells you how to mount other partitions or hard drives.

As far as I know you dont need to mount the swap partition anyway. You shouldent be able to go and look around it...

I think linux is really good using RAM. If you have 256 MB RAM it will try and use all of it, not just half of it. If you have 128 MB it will also make the best use of that.

---

### Post by cyclister on 2005-09-15
I have the same problem my systemoverviwer tells me that my swap is in use by 0,0 % :( but I have one.
In the installation I did as the questions asked me to do, and when it asked me to should I mount all partitons I did "klick" yes.But in some strange way I cant use my swap who is acctully bigger then it should :(
Why didnt it mount it self when it asked me if I wanted it to do that?
Strange  :???:

---

### Post by doclivingston on 2005-09-15
As others have mentioned, Linux tries to make the best use of your memory that it can - so the "free memory" will normally be close to 0. If you don't have any of your swap being used, or only a small amount of it, don't wory as everything is normal.

Swap partitions arent't mounted like normal filesystems are. If you want to check if it's being used as swap, open a terminal (System Tools->Terminal) and type in "swapon -s". If your swap partition is listed, then it is set up correctly.

---

### Post by SilentCacophony on 2005-09-15
Linux tries to use most of the available memory efficiently, taking up some of the free ram with buffers and cache to improve performance. If you run 'free' in a terminal, it'll show stats on it. Mine looks like so:
```
brian@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:        451728     297760     153968          0      10612     150172
-/+ buffers/cache:     136976     314752
Swap:       779112          0     779112
```

This means that I actually have 314752 *kilo*bytes free.  [*Whoops! Edited for correctness. Thanks, Jussi.*]

If you haven't used up all available memory, it won't need the swap space, so none will be used.

Also, the swap partition is not for storage. It is used as virtual memory, and can be used to save the session in some cases. It's reccommended to make the swap partition 1.5 to 2 times your total ram.

---

### Post by Jussi Kukkonen on 2005-09-15
[QUOTE=SilentCacophony]
```
brian@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:        451728     297760     153968          0      10612     150172
-/+ buffers/cache:     136976     314752
Swap:       779112          0     779112
```

This means that I actually have 314752 bytes free.[/QUOTE]

Just so no-one gets confused: *free* shows sizes in kilobytes by default, so that would be 314752 KB.

---

