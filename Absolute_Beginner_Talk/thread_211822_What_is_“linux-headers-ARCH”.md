---
title: "What is “linux-headers-ARCH”?"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by Gyrotwister on 2006-07-08
I’ve been having a go at compiling a driver for my Conexant HSF 56k HSFi internal modem in Ubuntu 6.06.  I’ve been advised to use Synaptic package manager to check that I have all the required packages installed.  They weren’t all installed, that explains why it failed to compile.  

[http://ubuntuforums.org/showthread.php?p=1197207#post1197207](http://ubuntuforums.org/showthread.php?p=1197207#post1197207)

The Howto which I’m following says I need…

1. build-essential
2. linux-headers-ARCH (ARCH is the result of "uname -r" command)
3. debhelper
4. fakeroot

build-essential was installed
debhelper was not installed but is available
fakeroot was not installed but is available
linux-headers-ARCH is the one which I’m confused about.  There are several files listed as linux-headers-xxxx but none tagged with the extension “ARCH”  

What is “linux-headers-ARCH”?  How do I install it?

---

### Post by dalee on 2006-07-08
Hi,

Arch, (architecture of processer) would be the kernel that is installed on your box. i.e. i386, i686, or k7.

So, if you are using the base Dapper install you would have the vanilla i386 kernel. If you installed an "optimized" kernel for your processer then you need to install the correct "arch" to match your kernel.

HtH,
dalee

---

### Post by Gyrotwister on 2006-07-09
Ok, my desktop is an Intel Pentium 4 CPU so I suppose I have the i386 kernel.  Ubuntu installed ok so I must have downloaded the correct iso file.  

I still do not understand though.  Would installing all the packages labelled "linux-headers-xxxx" mean that I have "linux-headers-ARCH" installed?  

How do I install this package?

---

### Post by Apple 101 on 2006-07-09
Look for it in Synaptic.

---

### Post by Gyrotwister on 2006-07-09
Thanks for the reply, but maybe I haven't explained my situation properly.  There is no shortage of linux-headers-xxxxx type packages avaliable to me in synaptic, infact I can count 17 of them.  

Some likley candidates are....
linux-headers-2.6.15-23
linux-headers-2.6.15-23-386
linux-headers-2.6.15-25
linux-headers-2.6.15-25-386
linux-headers-386

Which one/s should I install?

---

### Post by MrHorus on 2006-07-09
Type 'uname -a' and it will show you the version of the kernel that you are currently using.

The version you are using is the version that you will want to download :)

---

### Post by Gyrotwister on 2006-07-09
Thanks, that worked.  

The Howto which I've been trying to follow said to type in"uname-r".  Now I've learned that it should have been "uname -r". 

It's amazing how much a space (or lack of) matters when it comes to computing, especially when a novice like myself is blindly trying to follow instructions.

---

### Post by MrHorus on 2006-07-09
uname -r will show just the required information (-a shows all) and can sometimes be used as part of an update or installation script to automatically assertain what kernel or arch your system runs.

---

### Post by Gyrotwister on 2006-07-09
Winmodem is now also a Linmodem!

A good result, and a few things learned along the way!

Thanks again!

---

