---
title: "Install Ubuntu on 2006 Mac Pro with Dual Quad Core"
date: 2018-10-22
forum: Apple Hardware Users
---

### Post by Smack2k on 2018-10-22
New to the forums and fairly new to Ubuntu Linux in general...

I currently have Ubuntu 18.04 running on a machine I had from 2010 with an AMD Quad Core running at 3.2 GHZ, with 8 GB RAM.  Running pretty good I think and I am enjoying learning the Operating System and the UI.

I have a Mac Pro 1,1 from 2006 that has 2 Quad Core Xeons running at 2.83 GHZ with 32 GB RAM in it.  If I were to set this machine up with Ubuntu 18.04, would I see better performance, overall use?

What if I decided to set it up as a Linux Server for something like Minecraft?  Would it work well for that with the specs it has?

Appreciate the assistance as I decide what to do with the system...

---

### Post by hackerb9 on 2018-10-22
It's certainly possible, but I doubt you'd see much of a performance improvement. One cannot judge processors purely by their clockspeeds or core counts. The fact that the AMD processor is four years newer means it may be faster, for your workload even with less cores.  To know for sure, you'd have to actually benchmark the Minecraft server running on both machines. However, you can get a general estimate by looking at a website like cpuboss.com which has generic benchmarks. I put in a single X5365 vs. Phenom II X4 955 and it shows the Phenom beating a single Xeon.

But of course, you have two Xeons, which won't double your performance, but it will make your server more responsive if it is handling many tasks at once. Also, the 5365 processor has a nice big L2 cache which can make a big difference on certain compute tasks. 

By the way, what is the exact model of your processors? I notice that Apple sold the Mac Pro as a "quad core" machine with two processors, but what they meant was it had two dual core CPUs. Of course, since someone has maxed out the RAM in that machine, it's likely they upgraded the CPUs to quad core Xeons, as well.

---

### Post by oldfred on 2018-10-22
Moved to Apple Hardware sub-forum where those with a Mac may be able to help.

Some possibly similar systems:
       Installed Lubuntu 18.04 LTS on a MacBook Air 1,1 (early 2008) 
[https://ubuntuforums.org/showthread.php?t=2402179](https://ubuntuforums.org/showthread.php?t=2402179)
Old Mac with core2duo & 32 bit UEFI
[https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/](https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/)

---

### Post by Smack2k on 2018-10-22
> **hackerb9 said:**
> It's certainly possible, but I doubt you'd see much of a performance improvement. One cannot judge processors purely by their clockspeeds or core counts. The fact that the AMD processor is four years newer means it may be faster, for your workload even with less cores.  To know for sure, you'd have to actually benchmark the Minecraft server running on both machines. However, you can get a general estimate by looking at a website like cpuboss.com which has generic benchmarks. I put in a single X5365 vs. Phenom II X4 955 and it shows the Phenom beating a single Xeon.

But of course, you have two Xeons, which won't double your performance, but it will make your server more responsive if it is handling many tasks at once. Also, the 5365 processor has a nice big L2 cache which can make a big difference on certain compute tasks. 

By the way, what is the exact model of your processors? I notice that Apple sold the Mac Pro as a "quad core" machine with two processors, but what they meant was it had two dual core CPUs. Of course, since someone has maxed out the RAM in that machine, it's likely they upgraded the CPUs to quad core Xeons, as well.


I have two Xeon X5355's in my system, which are rated at 2.6 GHZ but the system says they are running at 2.83, so not sure if the system is seeing them wrong or what.  Either way, its two X5355s

---

### Post by hackerb9 on 2018-10-22
> **Smack2k said:**
> I have two Xeon X5355's in my system, which are rated at 2.6 GHZ but the system says they are running at 2.83, so not sure if the system is seeing them wrong or what.  Either way, its two X5355s

I'm guessing that whoever had this system before you wanted to squeeze every last drop of performance out and they overclocked the CPUs. Although I don't recommend overclocking for a server, in this case I wouldn't bother messing with it as Xeons have a pretty high heat tolerance.

Do try benchmarking and let us know how it compares to your AMD system. I suggest booting up Ubuntu from a Live USB to test it out before installing.

---

