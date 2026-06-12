---
title: "help: where is the kernel source code, thanks"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by tengxu on 2006-10-23
Hi all,

I am trying to install a software on my computer, the software ask me provide the "Directory containing linux kernel source code[]".:confused: 

So, where is the default directory for kernel source code in Ubuntu? :confused: I have to try to look at /usr/src, but its empty, is that mean I need to download it from somewhere. or maybe the source code hide in the other directory.

Thanks in advanced.

Cheers,
Teng

---

### Post by nickburns on 2006-10-23
you can get the linux header files with:

sudo apt-get install linux-headers-`uname -r`


and then the kernel headers are in /usr/src/kernel/include

---

### Post by yman on 2006-10-23
I don't know, but maybe it's the 4 KB file at /sys/kernel

---

### Post by David_T on 2006-10-23
If you are trying to install a kernel module of some kind, I would highly recommend apt-getting module-assistant, then just type its name on the command line after getting it installed.  It will walk you through the process of getting the kernel headers, selecting your module, etc.

The entire source code is available at kernel.org.

---

### Post by wkulecz on 2006-10-25
> **David_T said:**
> If you are trying to install a kernel module of some kind, I would highly recommend apt-getting module-assistant, then just type its name on the command line after getting it installed.  It will walk you through the process of getting the kernel headers, selecting your module, etc.

The entire source code is available at kernel.org.

Are you saying Ubuntu 6.06 runs an unmodified, box stock kernel?

--wally.

---

### Post by Ben Sprinkle on 2006-10-25
"Box stock kernal"
What the hell is that?
All Linux distro's use the Linux Kernal, it's how it runs!

---

### Post by Bachstelze on 2006-10-25
Nope, it doesn't, to my knowledge, only Slack and maybe Gentoo do.

**@tengxu,** installing the *build-essential* package should get you all the stuff you need.

**@synectics,** Ubuntu, like almost every other distro, does not run the kernel exactly as released by Torvalds and Co. The Ubuntu developpers do a great deal of work on it to make it fit the needs of the distro better. A "stock" or "vanilla" kernel means a "pure" kernel, downloaded from kernel.org. That's why you don't have a kernel available in the repos as soon as it's released on kernel.org.

---

