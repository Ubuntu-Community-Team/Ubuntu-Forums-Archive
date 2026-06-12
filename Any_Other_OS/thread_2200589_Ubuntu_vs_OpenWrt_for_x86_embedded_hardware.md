---
title: "Ubuntu vs OpenWrt for x86 embedded hardware"
date: 2014-01-20
forum: Any Other OS
---

### Post by charliemarquez on 2014-01-20
Hi,

what are the advantages in installing Ubuntu Linux on x86 based hardware compared to x86?
Besides the increased kernel loading time (which is likely to be smaller for OpenWrt), I don't see any advantage in installing openwrt in such devices
Do you agree?

---

### Post by TheFu on 2014-01-20
I doesn't look like your question is what you intended and I can't figure out what you meant. Please edit for clarity.

---

### Post by tgalati4 on 2014-01-20
openwrt has a much, much smaller footprint.  So unless you have 500MB of RAM, it would be difficult to run Ubuntu.  What embedded device did you have in mind?  Use the operating system that works with the hardware that you have.  Yes, booting any linux distro can take a lot of time, but most embedded devices are on 24/7.

---

### Post by charliemarquez on 2014-01-21
> **tgalati4 said:**
> openwrt has a much, much smaller footprint.  So unless you have 500MB of RAM, it would be difficult to run Ubuntu.  What embedded device did you have in mind?  Use the operating system that works with the hardware that you have.  Yes, booting any linux distro can take a lot of time, but most embedded devices are on 24/7.

Yes, I was also concerned by the footprint.
But my minimal ubuntu (obtained using debootstrap with the buildd parameter) just occupies 50Mb after the bootsrap
```

free -m
             total       used       free     shared    buffers     cached
Mem:           243         45        198          0         10         19
-/+ buffers/cache:         15        227
Swap:            0          0          0



```
I'm using an Alix [http://www.pcengines.ch/alix6f2.htm](http://www.pcengines.ch/alix6f2.htm) device, with 256 Mb of RAM

---

### Post by TheFu on 2014-01-21
> **charliemarquez said:**
> I'm using an Alix [http://www.pcengines.ch/alix6f2.htm](http://www.pcengines.ch/alix6f2.htm) device, with 256 Mb of RAM

If you have an Alix device, do yourself a HUGE favor and use pfSense. Seriously.
I know it isn't Linux based, but it is what security and network pros highly recommend for small/medium businesses using EXACTLY that hardware.  I know. 

Last year, I was designing a network upgrade for a Buddhist monastery in Nepal. It needed to work, have advanced features AND be secure.  This is a Tibetan Monastery with many monks in exile. Less than 50m away is a Chinese government compound with antennas pointed directly into the monastery.  I setup 3 different subnets (2 wifi and 1 wired) on the router to split off the working monks, paid clients seeking enlightenment and office traffic from each other. Priority was given to office traffic. Seems the monks like youtube and were sucking all the WAN bandwidth every evening - when the generator was powered. Nepal has rotating "power sharing" - 6 hrs with power, 6 hrs without that shifts 1 hour every day to be equally inconvenient for the entire country.

I asked for recommendations for both hardware AND software to provide a central router to them. The Alix2d3 was recommended by enough network/security people (white hats) and over 80% of the folks on the list strongly suggested pfSense. There were a few pushing Linux-based software too, but there are reasons for wanting a BSD-based solution.  Anyone can probably find the discussions in the archives.  BSD is known to have much better traffic shaping than Linux too.

I would make the same decisions again. Things turned out extremely well. The Ubiquity wifi APs are amazing. If I had a challenging wifi environment, I'd get some of that equipment for just under $100 - amazing. pfSense is very powerful on low resources.  It is known for slowing down when traffic gets really bad - like under a DoS attack - but not breaking.

I would avoid a complex Ubuntu install for a purpose-built hardware. Any added complexity is a real security risk and that needs to be a core consideration for a router.

---

### Post by CharlesA on 2014-01-21
I think TheFu already answered the question, but I'll just give a +1 to pfSense.

---

### Post by charliemarquez on 2014-01-27
TheFu,
I appreciate your help and I enjoyed reading your story. It was really interesting.
However I do not care too much on security aspects as I'm using the Alix boxes for wireless networking research.
So I need to compile my own software and use patched version of ath drivers.
My opinion is that with Ubuntu the Alix runs smoothly and I do not see much advantage in using openwrt. I wanted to hear your opinion

---

### Post by tgalati4 on 2014-01-27
That is impressive to get a custom, minimal Ubuntu install on such slim hardware.  If it runs smoothly then use it.  Because of the desktop and server roots of Debian and Ubuntu, there are many frameworks that are not tailored to embedded hardware.  But if you strip them out, and you can compile the kernel with the options and modules that you need, then go for it.  I had an embeddex x86 project for which I used Damn Small Linux as the base OS.  I did the development (compiling) on Ubuntu Dapper Drake and the resulting binaries were compatible with Damn Small Linux.  So that was a hybrid development model.  Ubuntu provides a nice development environment and DSL had a Damn Small footprint.

---

### Post by Julot on 2014-05-15
charliemarquez,  do not hesitate on your hardware and install OpenWRT to your motherboard, it's more than enough.

I am running OpenWRT successfully and stable in a portwell PPAP-100w,  This means:  Pentium III 1 Ghz (upgraded a few years ago from 466 Celeron to 1000 mhz - 100 mhz bus) with 128 MB SDRAM and using a 1 GB compact flash sandisk ultra II (only 54 MB used for the x86 combined  Openwrt img).  And an IDE 240 GB disk connected to the internal adaptor.

The little box runs transmission web based. a ftp server for my internal network (vsftpd), rsync for internal backups using ssh and vncrepeater, I use LuCI for administration.

cat /etc/banner
BARRIER BREAKER (Bleeding Edge, r40755)

root@OpenWrt:/etc# free
             total         used         free       shared      buffers
Mem:        124124       121872         2252            0          440
-/+ buffers:             121432         2692
Swap:       999932            0       999932

Top:
Mem: 121564K used, 2560K free, 0K shrd, 456K buff, 103216K cached
CPU:   4% usr   5% sys   0% nic  86% idle   1% io   0% irq   1% sirq
Load average: 0.06 0.14 0.20 2/45 7562

Even with transmission running all the time the small router is idling mostly.

root@OpenWrt:/etc# cat /proc/partitions
major minor  #blocks  name

   8        0    1000944 sda
   8        1       4096 sda1
   8        2      49152 sda2

I'm using the 5.32% if the compact flash therefore I think this ultra small OS can boot even in a 64 MB Compact flash!!.   Back to the future...

And it's not an old kernel:

Linux OpenWrt 3.10.36 #1 Tue May 13 07:08:43 UTC 2014 i686 GNU/Linux

I didn't measured yet the wattage but I think the whole little box complete is consuming about 60 watts when CPU is pushing or pulling RSYNC (80-100% used) and 20 to 25 watts idling with the IDE disk non sleeping.

No server today can beat this performance, If I want to improve this setup maybe I should use a router like a Buffalo or an Asus with the same config and I'm sure the maximum wattage would be 10-15 watts.  (or 5 watts using a TPL-MR3020).

The only linux OS I tested rather similar than OpenWRT in performance per watt is Debian squeeze with 486 kernel. But it uses 128 MB always and the whole point with OpenWRT is to avoid using a laptop or a server to do the same services like its VERY bloated brothers.

(Edited some typos).

---

