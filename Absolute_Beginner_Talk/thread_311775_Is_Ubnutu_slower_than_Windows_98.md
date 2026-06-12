---
title: "Is Ubnutu slower than Windows 98?"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Eldridge on 2006-12-03
I recently installed Ubuntu on a computer I use in the SETI distributed computing project.  My installation whent fine and I've been enjoying exploring this new operating system, I did not opt for a dual boot stystem and overwrote the existing Windows operating system with Ubuntu.  

I installed the SETI program on the disk and as part of the installation process the client program runs benchmarks on the system.  I was surprised to find that the benchmarks with Ubuntu installed on the same drive and processer was much slower than with the Windows operationg system:

Ubuntu:
[http://setiathome.berkeley.edu/show_host_detail.php?hostid=2904003](http://setiathome.berkeley.edu/show_host_detail.php?hostid=2904003)

Measured floating point speed 223.8 million ops/sec 
Measured integer speed 394.32 million ops/sec 

Windows 98
[http://setiathome.berkeley.edu/show_host_detail.php?hostid=2845470](http://setiathome.berkeley.edu/show_host_detail.php?hostid=2845470)

Measured floating point speed 398.32 million ops/sec 
Measured integer speed 701.2 million ops/sec 

This looks like a reduction in both floating point speed and integer speed operations of about 40% even though I added additional memory when I installed Ubuntu.

My motherboard came with a disk of drivers, which I did not install after I changed to Ubuntu.  Should I have installed the motherboard drivers?  I was assumming they would no longer work or be necessary with Ubuntu.

I'm wondering if I made some mistake or ommitted something when I installed Ubuntu or if the OS is just inherently slower.  Is there some component (other than the GUI) I could uninstall to improve my speed?  If anyone has any suggestions it would be greatly appreciated, but even if there is no solution I'm going to stick with Ubuntu for this computer, I'm learning a lot and have been really impressed with it.

Eldridge

---

### Post by ragnar_123 on 2006-12-03
could it be that you've installed slower memory blocks?
example: before 256mb pc 3200, now 512 pc 2100, or something like that, which means that they will set down you cpu speed.

sry for my bad english..

---

### Post by 56phil on 2006-12-03
Firstly, welcome to Ubuntu.:) 

Secondly,Linux has a sophisticated scheduling process that puts windows to shame. Even so, I can't imagine a forty percent reduction in the benchmark. Did you notice the priority of the benchmark program? Also, what other processes were running at the same time? I find that Xorg and Gnome chew up a fair number of CPU cycles on my system.

Well, it's not much, but I hope this helps.

---

### Post by apjone on 2006-12-03
Which version of Ubuntu did you install??

---

### Post by David Corrales on 2006-12-03
Doesn't look like the same system to me. Different processor, memory and cache for starters.

---

### Post by Eldridge on 2006-12-03
The version I installed was 6.06 LTS.

Yes, the benchmark did report the processer differently between the two installs, but it really is the same processer.  Windows called it a Pentium II, but Ubuntu more accurately reported it as Pentium III (Katmai).  I'm not sure what you mean by cache, is that something I can change or check in my BIOS setup?  I didn't make any changes.

I ran the benchmark for Ubuntu with a fresh install without any other programs running.

I do have mixed memory modules in the box but the only one that I added between the two installs matched the fastest one already in the box.  I might go ahead and pull the slower one and see if that helps.

Thanks for all the feedback.

---

### Post by Eldridge on 2006-12-03
David,

I see what you're talking about now, thats bound to be the problem, now if I can just figure out how to fix it.  Thanks for taking such a close look at the benchmark links I posted.

Operating System Linux 
2.6.15-27-386 
Memory 377.28 MB 
Cache 512 KB 
Swap space 360.79 MB 

Operating System Microsoft Windows 98 
, (04.10.1998.00) 
Memory 255.52 MB 
Cache 976.56 KB 
Swap space 1792.48 MB

---

### Post by Oki on 2006-12-03
Eldridge;
Could you pl. tell me how to install SETI?
I have tried the SAutomatic2 version, but with no luck.

---

### Post by steve.horsley on 2006-12-03
Could it be the power management? 

I have an Athlon so this may be a little different, but most things tell me I have a 1GHz CPU. However, if I set off a task that uses lots of CPU, now everything tells me I have a 2GHz CPU. If things get busy, Linux doubles the clock CPU rate. If they stay busy, the fan slowly speeds up until the windows are rattling. I guess Intel has similar power management capability, but I also guess that Win98 doesn't.

If this is the case, then when it really gets going, SETI will cause the OS to turn up the clock rate and you'll get the full oomf.

---

### Post by mikerduffy on 2006-12-03
> **steve.horsley said:**
> Could it be the power management? 

I have an Athlon so this may be a little different, but most things tell me I have a 1GHz CPU. However, if I set off a task that uses lots of CPU, now everything tells me I have a 2GHz CPU. If things get busy, Linux doubles the clock CPU rate. If they stay busy, the fan slowly speeds up until the windows are rattling. I guess Intel has similar power management capability, but I also guess that Win98 doesn't.

If this is the case, then when it really gets going, SETI will cause the OS to turn up the clock rate and you'll get the full oomf.

I've noticed that too.  Right now in KDE (kubuntu 6.10), the power management icon in the system tray says that my cpu is currently running at 800MHz.  In Windows XP, the cpu runs at 800MHz only when running on battery power, and 3.2GHz when plugged in.

---

### Post by Eldridge on 2006-12-03
Oki,

There was a lot of confusing instructions on the SETI site about installing it on Linux.  I first tried the instructions that were in the area where you download the client and I had a lot of problems.  Of all the different explanations of how to get it working this is the one that worked for me.  It didn't assume any previous knowledge of Linux and walked me through it step by step.  Hope this helps:

[http://boinc-wiki.ath.cx/index.php?title=Installing_The_BOINC_Client_Software_on_Linux](http://boinc-wiki.ath.cx/index.php?title=Installing_The_BOINC_Client_Software_on_Linux)

It turns out I didn't have to deal with a command line at all.  Download, make the installer program executable, run the installer to place the client where you want it.  Then I was able to run the client and the manager from within the GUI.  Why there were other instructions making it so much more difficult I can't understand.

Eldridge

---

### Post by IYY on 2006-12-03
Ubuntu is a modern operating system, so it is slower than Windows 98, especially on older hardware. Windows 95 and DOS are even faster. 

However, much of the slowness has to do with a larger and more complete desktop environment and window manager. If you switch to something like XFCE, or the even lighter IceWM or Fluxbox, you will notice significant improvements, especially if your system lacks in memory.

---

### Post by livinginx on 2006-12-03
Seems to me like one processor is a PII and the other is a PIII along with what everyone else said about memory, but the system with the lower hardware specs is Win98?

---

### Post by Sef on 2006-12-03
> Seems to me like one processor is a PII and the other is a PIII along with what everyone else said about memory, but the system with the lower hardware specs is Win98?

Yes, but more cache, swap, and ram for Windows 98.

> Ubuntu is a modern operating system, so it is slower than Windows 98, especially on older hardware. Windows 95 and DOS are even faster.

However, much of the slowness has to do with a larger and more complete desktop environment and window manager. If you switch to something like XFCE, or the even lighter IceWM or Fluxbox, you will notice significant improvements, especially if your system lacks in memory.

Very true.  I have an old laptop (700MHz and 128 ram,) and Ubuntu is so sluggish on it, but Xubuntu goes so fast.

---

