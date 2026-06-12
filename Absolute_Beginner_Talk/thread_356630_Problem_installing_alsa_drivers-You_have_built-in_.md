---
title: "Problem installing alsa drivers-You have built-in ALSA in your kernel."
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by cgreer on 2007-02-08
On my everending quest to insall these alsa drivers I have done a couple things that might be usefull to know before I post the current problem.

1. tried to ./configure the alsa-driver folder in my home directory but needed a C compiler?  So I did apt-get install build-essential.

2. Tried again to do ./configure but it says I was missing version.h so I did the code: apt-get install linux-headers

3. Tried once more, figured out that I needed to include the --with-kernel=dir option because the linux-headers folder was named linux-headers-something else instead of just "linux", which is where it was looking by default.  (Is there anyway I can rename the folder "linux"?)

OK, no I do ./configure and it goes past the version.h part, but it still doesn't seem to "finish".  This is what it gives me:
```

checking for directory with kernel source... /usr/src/linux-headers-2.6.15-27
checking for directory with kernel build...
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.15.7-ubuntu1
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... yes
configure: error: You have built-in ALSA in your kernel.

```

......Being the noob I am, I'm pretty much clueless.  If anyone can help me I would really appreciate it.  If you would like me to post the entire code or include any information please don't be afraid to ask.

Thanks,
CG

---

### Post by daou on 2007-02-08
I believe, like configure just told you, that the 2.6.15 Ubuntu/Linux kernel comes with ALSA drivers. Why do you need to compile them?

BTW, you aren't a hopeless noob if you got _that_ far in your build process. Successfully compiling a program, much less a driver on Linux is quite a milestone.

---

### Post by cgreer on 2007-02-08
I need to recompile the a newer version.  If it told me that the kernel comes with Alsa drivers are they the newest version?  Is there a terminal code that I can use to figure out which version I currently have installed?

Thanks for the help and encouragement.




PS: what does all this mean (I'm curious):

checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5) //what is the GCC? What's the difference between the versions?

*** NO PREDEFINED KERNEL COMPILER IS DETECTED //Am I supposed to have a predefined kernel compiler?
*** Assuming the same compiler is used with the current system compiler. //huh?

*** Please make sure that the same compiler version was used for building kernel. //how would I do that?

---

### Post by daou on 2007-02-09
> If it told me that the kernel comes with Alsa drivers are they the newest version? Is there a terminal code that I can use to figure out which version I currently have installed? 
Your kernel probably doesn't have the newest alsa drivers because the kernel itself is quite outdated (in kernel development time, but don't worry, it should still be fine). You can test what version your alsa driver is:

"modinfo snd"

snd is the name of the alsa-module, at least on my system. It will give you a listing with quick info.

> what is the GCC? What's the difference between the versions?
 gcc = GNU Compiler Collection
This is a bunch of (great) tools that allows you to build anything from programs to drivers to the kernel itself, even for embedded systems (then it needs additional bits). The versions don't usually have much that changes whether your programs will be built correctly. The Linux kernel itself is so dependent on a certain type of gcc, that big changes in it would make quite a panic there. And that answers the last question you had. Yes, you have the same compiler (gcc) that was used to build the kernel itself. I am assuming, but its like assuming the sun will rise tomorrow because it has done so faithfully in the past.

---

