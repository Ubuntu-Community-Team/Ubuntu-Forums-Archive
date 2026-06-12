---
title: "Kernel? Big Difference? Distro to Distro?"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by Weav on 2005-09-12
I've been using Ubuntu for a while, but I was just wondering what is the primary difference between distro from distro, say from Ubuntu to Suse.

I know what a kernel is and what its purpose is, but is that the main difference the kernel and how it composes or performs? Or is it instead the applications installed or maybe even the GUI?

Thanks for any information.

---

### Post by cwaldbieser on 2005-09-12
[QUOTE=Weav]I've been using Ubuntu for a while, but I was just wondering what is the primary difference between distro from distro, say from Ubuntu to Suse.

I know what a kernel is and what its purpose is, but is that the main difference the kernel and how it composes or performs? Or is it instead the applications installed or maybe even the GUI?

Thanks for any information.[/QUOTE]
I would say that it is the applications installed, but also the culture of the community.  For example, in Slackware, there is a very "hands on" approach to installing and configuring software.

---

### Post by aysiu on 2005-09-12
Package management.
Defaults (what programs are included, what the desktop looks like, etc.)
Support and community.
Number of install disks.
Cost.

---

### Post by Weav on 2005-09-12
[QUOTE=aysiu]Package management.
Defaults (what programs are included, what the desktop looks like, etc.)
Support and community.
Number of install disks.
Cost.[/QUOTE]
Well I really do not understand why there are so many distros. Ok I install Enlightenment of KDE onto Ubuntu, have I just changed my "distro"? It just doesn't make sense, is the word distro too loosely used and its basically just a combinatino of all the above?

---

### Post by aysiu on 2005-09-12
Well, yes and no.

I mean, one of the things that defines a distro is its defaults. Mandriva defaults to KDE. Blag defaults to Gnome. You can install Gnome on Mandriva, and you can install KDE on Blag, but those aren't the *defaults*.
Some people complain because Ubuntu doesn't come with proprietary multimedia codecs *by default*. They can be easily installed, though.

On the other hand, even though they really have the same base, Ubuntu and Kubuntu are separate distros in a sense, only because one defaults to Gnome and another to KDE.

A lot of distros are based off of other distros. Knoppix is based on Debian, and Mepis is based on Knoppix.

Usually what sets a distro apart from another are its defaults *and* the package management. Many people, for example, prefer Debian's apt-get to Fedora's Yum or Mandriva's urpmi. In Gentoo, you Emerge.

Ultimately, they all use the Linux kernel and can be set up to look the same and almost completely behave the same, but defaults make a big difference. I'd much rather install Ubuntu than Slackware, even if they both end up being Gnome desktops with the same programs.

---

### Post by Qrk on 2005-09-12
Don't forget about hardware detection. 

Basically a distro is some combination of included packages (Gnome, OO.o, xorg etc) combined with some form of package management (rpm or deb usually) with some way to install it, (like Anacanda, YAST or the Debian intstaller,) all tied neatly with a bow and made into an iso file. 

But there are differences enought to make each distro unique. For instance Ubuntu uses basically the same installer as Debian, has the same package management and similar availabe packages. What makes it different? Well, it has newer packages, like the latest version of Gnome, and some different packages, like xorg. It also ties it together neatly with a bow and puts it on one cd with a wide collection of programs devolped for Ubuntu, like update manager. 

To a newbie, there is a huge difference between distros, because they all install differently and change their "look and feel" But after trying a few distros out, they are basically all very similar. Gnome on Fedora isn't all that different from Gnome on Ubuntu, and it isn't any harder to type apt-get or yum. 

Really, once you start to use Linux, the main difference is the community. Most package managers are really quite good these days (although I still rank apt the best) and you can configure one to look like the other pretty quickly. But the community is distro specific.

Take Ubuntu. It doesn't have the easiest install, that would be PCLinuxOS or Mandrake. It is not the most configurable, which would be Gentoo or Slackware. It shares apt with Debian and just about every other Debian derived distro on the planet. And it doesn't have all the features of SUSE. And really, it doesn't even have the largest community like Fedora does. What makes Ubuntu such a great distro is that it excells in many areas and doesn't really fail in any.

---

### Post by cwaldbieser on 2005-09-12
[QUOTE=Weav]Well I really do not understand why there are so many distros. Ok I install Enlightenment of KDE onto Ubuntu, have I just changed my "distro"? It just doesn't make sense, is the word distro too loosely used and its basically just a combinatino of all the above?[/QUOTE]
It is somewhat like eating at an Italian resturaunt.  I have a good idea what will be on the menu, but little things differentiate each place.  I may have a favorite that is based on the atmosphere, the sauce, the noodles, or the courteous staff.

---

### Post by aysiu on 2005-09-12
[QUOTE=Qrk]What makes Ubuntu such a great distro is that it excells in many areas and doesn't really fail in any.[/QUOTE] Or when it does "fail," it's usually on purpose, because it's committed to being free.

---

### Post by poofyhairguy on 2005-09-12
[QUOTE=Weav]Well I really do not understand why there are so many distros. [/QUOTE]

Because all the software is free to use, so lots use it to make different OSes.



 >  Ok I install Enlightenment of KDE onto Ubuntu, have I just changed my "distro"? 

No. You are still using Ubuntu then. If you switch from SUSE to Ubuntu, you switched distros. Someone else made each of them.

Link to help:

[http://en.wikipedia.org/wiki/Linux_distro](http://en.wikipedia.org/wiki/Linux_distro)

---

### Post by Weav on 2005-09-12
Ok thanks for all the information everyone, I know now what loosely defines a distro and all the things attached to it. Thanks!

---

### Post by weasel fierce on 2005-09-13
I think its a lot about attitudes and goals, of the designers.

---

### Post by savage on 2005-10-12
I found this thread because I was searching for information on what; differences between distro kernels is if anything. I'm reading Linux Cookbook by Carla Schroder and in chapter 10.1 she says:

> 
The different Linux distributions modify kernels to varying degrees. Red Hat, SuSE, and Mandrake ship heavily modified kernels. Debian and Slackware mess with them only a little bit. It's possible that installing a vanilla kernel from [http://kernel.org]("http://kernel.org") will cause things to break on distributions that use modified kernels, so it's better to use kernel sources for your distribution. 
Where is Ubuntu in the kernel scheme? Is there a place to find out what changes are made, do I even need to worry about this? Is Linux Cookbook wrong? If I'm supposed to use distro kernels is there an Ubuntu specific howto on taking 2.6.11-1 to 2.6.11-8+?

update: [http://www.ubuntuforums.org/showthread.php?t=43065](http://www.ubuntuforums.org/showthread.php?t=43065) mentions how to use the official ubuntu kernel

---

### Post by matthew on 2005-10-12
> **savage]I found this thread because I was searching for information on what said:**
> http://www.ubuntuforums.org/showthread.php?t=43065[/URL] mentions how to use the official ubuntu kernel
I can't answer all of your question, especially the part about specifics and the Ubuntu kernel. Hopefully someone else will chime in with that info.

The book you are reading is right to a point, especially if you use certain hardware. For example, I know the Ubuntu kernel has complied in as a module support for the Intel ipw2200 wireless card. This is a proprietary driver and not in the vanilla kernel. If you installed Ubuntu on a laptop that had that kernel and all was working well and then compiled a new kernel your wireless would not work until you added in the necessary driver yourself. That is an example of potential breakage.

However, if you have pretty standard hardware that is well supported by Linux in general it probably won't make a difference which kernel you use--one from your distro or one from vanilla sources that you compile. There may be speed differences if you compile your own.

Another issue is security updates. If you use a standard kernel from your distribution you should receive occasional security updates to that kernel when they are released without having to recomplie a new kernel from scratch. That's a big time saver and another great reason to stick to your distro's kernel.

I hope that helps a little bit.

---

