---
title: "Cannot Record with JACK"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by seagullplayer77 on 2008-03-09
First things first: I'm pretty new to this Linux stuff, although I've been using it successfully (for the most part, anyway) for a few months now. There's only one major thing that I can't get to work, and after about two months of spending my weekends and spare time scouring various forums and Websites for answers, I've finally reached the end of my rope. 

Here's what I have managed to do:

I've gotten JACK up and running with a satisfyingly low latency, so that's not a problem, and I've managed to get Ardour and Hydrogen to link up using JACK. Ardour will record Hydrogen, and I can play back what I record using Ardour, so I have audio out. 

Here's my issue:

I can't get my external mic port to record with JACK. It just won't do it. I'm running Ubuntu Studio, mainly because I wanted all of the audio apps to do some recording with, but without a mic port...well...

Since JACK records fine if I'm linking up two pieces of software, I'm not sure that JACK is the culprit, but I'm pretty new to this stuff, and right now, I just want to get it fixed.

I don't know how useful this information will be, but I've got my Ubuntu Studio running on a Toshiba A105-S4064 laptop. I'm fairly certain that the audio card is a Realtek ALC861. 

I'd be more than happy to provide any other necessary info, just as long as I can get this thing fixed. I've been dying to record something for weeks, but this problem had driven me up the wall. Please help!

OK...I decided I'd include this information too. Maybe it'll help. I tried to install some Realtek drivers (don't know if that's the problem, but like I said--I'm trying everything), and when I tried to configure, this is what it gave me:

checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/chrkal/Desktop/alsa-driver-1.0.4
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

I've got the feeling that the fact that /usr/src/linux is significant somehow...Like I said, I'm pretty new to this stuff, so I'm sorry if this I made a dumb mistake somewhere along the line.

---

### Post by seagullplayer77 on 2008-03-10
bump

---

