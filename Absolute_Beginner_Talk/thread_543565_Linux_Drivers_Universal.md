---
title: "Linux Drivers Universal?"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Officer Dibble on 2007-09-05
Are Linux drivers universal, i.e., a piece of hardware that states compatibility with Linux, will its drivers be compatible with any distro of Linux?

There isn't any particular piece of hardware I am referring to at the moment... just curious...

---

### Post by ggaaron on 2007-09-05
To be exact, linux is only a small part of GNU/Linux distributions - it is the kernel and most drivers are handled by kernel, other ones are most often build against you kernel too. Most distributions use the same kernel, it may have some patches from some distribution but is is basically the same thing, so drivers should work with any distribution, because all distributions use the same kernel.

This is just theory though, it can be not true because for example ubuntu ships binary, pre-compiled packages, so does debian, they both use .deb files, but if you install a debian package on ubuntu you'll probably brake your system. The same application, but build differently, so if your drivers depend on a system package they may be able to use one from some distributions, not from the other.

To be optimistic in the end: most drivers are just build in kernel and if they are not, then probably your distribution ships a package with this drivers and it should work for the given distribution=)

EDIT: "a piece of hardware that states compatibility with Linux" - have you seen actually something like that? I haven't=D

---

### Post by Officer Dibble on 2007-09-06
I have seen the "Linux Compatible" statement on hardware, and if pressed then I could search for some.

As there is the risk of 'breaking' my system because of a wrong driver, is there anyway of checking other than Ubuntu being specified? When you say "Breaking", are we talking complete reinstall required?

---

### Post by ramjet_1953 on 2007-09-06
ggaaron, it is not quite true about installing a .deb package that is not in the Ubuntu repositories and it breaking your system.

In most cases, it will run fine, providing you satisfy the dependencies.

If the dependencies are not satisfied, it will tell you and the package will not be installed.

After all, Ubuntu is a fork of Debian.

I have installed dozens of .deb packages from a variety of sources and have had very few problems. 

I have even used alien to convert .rpm packages to .deb, again with great success.

Of course, the best way to install a package that is not in the repositories is to download the source tarball and compile it yourself. This will optimize it for your particular installation, but is also full of pitfalls and frustrations for those not familiar with compiling.

Regards,
Roger 8)

---

### Post by ggaaron on 2007-09-06
I've seen many warnings about installing not Ubuntu .deb's and I've had some problems myself, not a complete reinstall, but installed piece of software not working and programs depending on it not working either.

But respect for you for doing such things with success=)

---

### Post by Harpoon on 2007-09-06
Dibble:  To answer your question directly, yes.  If a manufacturer states that the device is supported in linux, that means the drivers to make the device work are available and that device can be made to work in any distribution.  The only thing you might want to look out for is something like "kernal 2.x or above"  which means that you may (probably) run into problems if you are running an old version.  This is equivalent to a box that says "supports W2K/XP or better."

Personally, I never buy devices that do not have linux support, even when they are destined for use on windoze only machines.

---

