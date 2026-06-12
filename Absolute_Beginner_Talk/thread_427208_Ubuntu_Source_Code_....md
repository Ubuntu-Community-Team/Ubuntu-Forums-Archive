---
title: "Ubuntu Source Code ..."
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-04-29
I have run Ubuntu dual boot with Windows for several months now.
Being a C++ programmer, I am interested in the source code for Ubuntu.

Since WIndows source code is considered a "Microsoft secret", I like the idea that Linux is considered "open source".

Where is the Ubuntu source code?  Any websites devoted to understanding the code?

Thanks

Carl

---

### Post by Tomosaur on 2007-04-29
Ubuntu is a Linux distribution. All Linux distributions use some version of the Linux kernel. The latest kernel source code is always available from [http://www.kernel.org](http://www.kernel.org). The kernel is actually what people mean when they say Linux. Ubuntu, and any other Linux distribution, is really just a set of programs bundled with the Linux kernel - although most distributions do make some modifications to the kernel, and to the programs which they package alongside it.

All source code to everything which comes with Ubuntu is available in the repositories. Click System > Administration > Synaptic Package Manager, and do a search for 'kernel source code', or the source code for any program you wish to download. You may need to enable the 'src' repositories via the preferences/settings menu first.

Downloading the kernel source code via kernel.org will mean you have the latest kernel version source, but it may not work properly with Ubuntu once you compile and install it. The kernel source from the Ubuntu repositories is pretty much guaranteed to work once compiled and installed, but it is an older kernel version. The kernel.org source is updated very regularly, while Ubuntu kernel updates can have larger gaps between them.

If you are interested in modifying Linux, you may be more suited to the Gentoo distribution, which is essentially totally source-based. You are required to compile and install pretty much everything yourself - making it ideal for people who like to tweak and understand the software they run. Ubuntu is not really targeted at people who wish to modify everything - because it is fairly heavily modified as it is, which allows such a high success rate 'out of the box'.

One website you may be interested in, however, if you want to get into Ubuntu development / bug fixing etc, is [http://www.launchpad.net](http://www.launchpad.net).

---

