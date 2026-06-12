---
title: "winecfg crashing with a page fault"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by cooper6581 on 2007-06-18
Hello All!  Has anyone experienced issues with winecfg crashing?  I've installed wine a lot of times with different distros, and compiled from source but never ran into this problem.

I originally installed just with apt-get install wine, and after the crashes, added the repository listed on the wine site for debian and ubuntu.  I installed the latest version from there and I'm running into the same issue.  I can't seem to find any information about this.

cooper@banana:~$ winecfg
wine: creating configuration directory '/home/cooper/.wine'...
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7cf9c23 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7cf9c23).

<end snip>

I'm currently running the ati binary driver.  Does anyone think this might have something to do with the crash above?  Thanks in advance for any insite that can be provided.

---

### Post by cooper6581 on 2007-06-18
FYI, just to see if it was a problem with the packages, I just compiled the latest stable version of wine and have the exact same issue.

```
cooper@banana:~$ wine --version
wine-0.9.39

cooper@banana:~$ winecfg
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7d91c23 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7d91c23).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7d91c23 ESP:0033edfc EBP:0033ee18 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:b7e60ff4 ECX:00000000 EDX:00000009
 ESI:00000033 EDI:00000000
Stack dump:
0x0033edfc:  b7d91955 00000000 7c01bb60 0033ee18
0x0033ee0c:  7e4303bc 00000033 00000000 0033ee98
0x0033ee1c:  7e3f7f92 00000000 00000075 7c054430
0x0033ee2c:  00000001 7c04ab98 00000000 00000000
0x0033ee3c:  00000000 7c054430 7c01bb60 00000075
0x0033ee4c:  0033ef54 0033eea8 0033ef44 0033ef24
```

---

### Post by cooper6581 on 2007-06-18
In case anyone stumbles accross this post, I found this doesn't occur with the open source ati driver (radeon).  There is a setting for your xorg.conf which the winehq wiki states, but it didn't work for me.  Another reason to hate ATI  :)

[http://wiki.winehq.org/fglrx](http://wiki.winehq.org/fglrx)

---

### Post by Max Spain on 2007-06-24
Interestingly enough, I have the same problem, but I am using a via system instead of ATI.  It was also working fine until one or two kernel updates ago :confused:  I have tried uninstalling and reinstalling to no avail.

---

### Post by Max Spain on 2007-06-24
Hehe, just fixed it by commenting out Load DRI in my Xorg.conf file ;)

---

