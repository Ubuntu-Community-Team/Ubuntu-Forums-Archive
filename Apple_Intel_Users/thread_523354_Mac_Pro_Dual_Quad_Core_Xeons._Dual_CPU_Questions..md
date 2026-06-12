---
title: "Mac Pro Dual Quad Core Xeons. Dual CPU Questions."
date: 2007-08-11
forum: Apple Intel Users
---

### Post by JesterDev on 2007-08-11
I'm planning on buying a Mac Pro soon, and I'm looking at getting it with dual 3.0GHz Quad Core Xeons (8 Cores total). Now from my personal research; and I hope I understand this correctly. Going down this path will be like having 8 3.0Ghz CPU's right? (Sounds like overkill personally but I like it. ;D ) At first I thought I would be running a 24Ghz Mac, but this is not the case (acually I know it was not the case, but can't blame me for trying). So I'm wondering what speed will this Mac be running at? 3.0GHz, 6.0Ghz?

I'm just trying to understand how Dual CPU's work. I know that when the load becomes too heavy for one CPU the other is used to carry the remaining load. But what about in a quad core system, or is it the same?

I'm thinking about the future here, not the present. As of right now it's major overkill I know. But this is a $6000 system, so I don't plan on buying another for quite a few years.

My next concern is Ubuntu. Will I have any issues running Ubuntu on this Mac? I've heard of people having issues with some distro's and dual core CPUs, so perhaps 8 cores will also pose problems. Then again this was awhile back and has most likely been resolved.

Anyway here are the specs:

# Two 3.0GHz Quad-Core Intel Xeon
# 4GB 667MHz DDR2 fully buffered ECC memory (4 x 1GB)
# 500GB 7200-rpm Serial ATA 3Gb/s
# 750GB 7200-rpm Serial ATA 3Gb/s
# 2 ATI Radeon X1900 XT 512MB of GDDR3 (2 x dual-link DVI)
# Apple Cinema HD Display (23" flat panel)
# One 16x SuperDrive

---

### Post by benanzo on 2007-08-11
First of all, this is way overkill.  But you know that.  Ubuntu shouldn't have any problem on an eight-core machine.  SMP (symmetric multiprocessing) is pre-compiled into the generic Ubuntu kernel.

Basically you will have eight processors that run at 3.0Ghz.  None of them will work in any kind of tandem-way that will multiply their clockspeeds.  Almost no desktop OSs (Windows, Mac or Ubuntu) efficiently deal with multiple processors (or even mult. threads in a single processor).  That is to say that there are almost no desktop applications that are capable of taking advantage the performance gains of such a system.  The only place you will likely find that kind of performance is in specially compiled server applications running on a seriously tricked out GNU/Linux or UNIX kernel.

Keep in mind that the I/O on your disk drives, your bus speeds, your RAM clocks are going to be far slower that the collective computing ability of your processors.  I seriously doubt you will see any measurable performance gain over a simple dual core system.  You will have the best performance if you get dual 10,000RPM drives in a RAID0 array (striping) with about 4-8 gigs of RAM.  Anything less than that and your CPU(s) will be constantly waiting for your hard disks/RAM to catch up.

Have fun though!

---

### Post by JesterDev on 2007-08-12
Thanks for the advice. I really just wanted a single Quad core CPU, but all the Mac pro's come with dual CPU's. Perhaps dropping down to a Dual 2.66GHz Dual Core would be the proper way to go. They don't seem to offer a 3Ghz dual core model. 

Raid is an option if I want to drop down another $1000, but I'm sure I can find cheaper hardware somewhere else.

---

### Post by ssam on 2007-08-13
i am using one of these [https://secure.dnuk.com/systems/w320-he.php](https://secure.dnuk.com/systems/w320-he.php) with a dual core 2Ghz xeon. it is the same processors and chipset as the mac pros.

currently nearly all desktop software can only use a single core. however on a linux system there are usually many processes running (run top in a terminal). with a dualcore the main application that you are using (eg GIMP) can grab 100% of one of the cores, and all other tasks can be pushed to the other core. this wont double the speed of the gimp, but it may make it a bit faster. in going from 2 ->4 core the improvement will be less than in 1 -> 2.

[OpenMP]("http://en.wikipedia.org/wiki/Openmp") has recently been added to GCC (the most common compiler on llinux). i am hoping that this will mean soon things like the gimp will add multiprocessor support. then a single program will be able to efficiently use many processors.

one place where a dual core helps a lot for me is converting RAW files from my camera into JPEG. I have a script that uses dcraw. By making the script work on two files simultaineously it takes half the time to run. Another place is compiling. make has an option to set more than one task going at a time.

---

### Post by russo.mic on 2007-08-13
Now really,  why would the GIMP ever need serious multi-processor support?

---

### Post by macaholic on 2007-08-13
I have a Mac Pro 2.66 ghz quad core, and in many everyday applications (web browsing etc.) you won't see tremendous gains. The 8-core systems are aimed at people usually doing proffesional video editing or photo editing w/ programs that take full advantage of those cores. Eventually more programs will take more advantage of more than two cores, but right now if you aren't doing anything that is process heavy there is no reason to go for that much overkill.

---

### Post by ssam on 2007-08-15
> **russo.mic said:**
> Now really,  why would the GIMP ever need serious multi-processor support?

doing large operations on large images uses lots of cpu. for some actions the image can be broken up in to tiles, and each one processed independantly. sounds to me like the perfect application to benifit from multiple CPUs.

---

