---
title: "Software Installation"
date: 2005-06-24
forum: Absolute Beginner Talk
---

### Post by kook44 on 2005-06-24
Hello-
I've dabbled in varios distros of linux over the years, and have basic command line experience as an end-user, so I feel I have a basic understanding of linux, but one thing I could never fully grasp is how software is installed.

I get the idea of the traditional configure,make,make install method, but what about these package managers?  & Why do they seem to be the preferred method? I understand the idea that they can check for dependencies, etc.  But do software developers have to make installation packages for each and every distro?  If the distros share the same kernal, then shouldn't the software the same for each?  This doesn't seem very "open" or "free (as in free speech ;) )" to me. 

I'm a little confused

---

### Post by estel on 2005-06-24
Yours points are valid, and are often brought up.
More often than not though, there will be a separate group of people who create and  maintain the packages from existing source code. There's a group of these for Ubuntu, and much of their work is taken up with packaging what the Ubuntu developer's make.

I think the main reason that distros have different package systems is that a new distro will start with a new package system, that it thinks is better than any others. Older distros don't want to change their very foundation.

---

### Post by jdong on 2005-06-24
[QUOTE=kook44]Hello-
I've dabbled in varios distros of linux over the years, and have basic command line experience as an end-user, so I feel I have a basic understanding of linux, but one thing I could never fully grasp is how software is installed.

I get the idea of the traditional configure,make,make install method, but what about these package managers?  & Why do they seem to be the preferred method? I understand the idea that they can check for dependencies, etc.  But do software developers have to make installation packages for each and every distro?  If the distros share the same kernal, then shouldn't the software the same for each?  This doesn't seem very "open" or "free (as in free speech ;) )" to me. 

I'm a little confused[/QUOTE]
The software contained in these specialized packages have been tweaked to integrate with your distro, whether it's installing files in specialized places or making two programs work together.

Each distro likes to ship with different versions and combinations of libraries, so applications using these libraries must be compiled against the correct libraries, so NO, not all distributions are binary-compatible with others.

This is a concern/weakness of Linux we all want to address. The LSB (Linux Standard Base) is a set of standardized libraries and environments that all Linux distributions should comply with. Ubuntu supports the LSB but isn't certified by it yet.

---

### Post by kook44 on 2005-06-24
Estel & Jdong -
thanks I'm beginning to understand

So i'm guessing there is a rule of thumb- when software is available as a package for your distro, it will save you some headaches, and generally be a clean install. Wheras software that is available only as source will work on any distro - but you may have to roll up your sleeves and do some configuration on your own.
Am I close to the mark here?  :-k 

What about software that you install as a package, but you would then like to install a newer version?  I guess in the case of Ubuntu, you can just download the updated package from Ubuntu, right?

---

### Post by jdong on 2005-06-24
[QUOTE=kook44]Estel & Jdong -
thanks I'm beginning to understand

So i'm guessing there is a rule of thumb- when software is available as a package for your distro, it will save you some headaches, and generally be a clean install. Wheras software that is available only as source will work on any distro - but you may have to roll up your sleeves and do some configuration on your own.
Am I close to the mark here?  :-k 
[/quote]
Exactly. And if you do have to compile from scratch, please install into the /usr/local tree ,or use the "checkinstall" program. Both of these methods guarantee that your package doesn't cause problems later down the road.
> 
What about software that you install as a package, but you would then like to install a newer version?  I guess in the case of Ubuntu, you can just download the updated package from Ubuntu, right?


Check out the Ubuntu Backports Project, which updates software for the current stable release. You may make requests for Breezy-to-Hoary backports at the Backports forum section :)

---

### Post by poofyhairguy on 2005-06-24
[QUOTE=kook44]
So i'm guessing there is a rule of thumb- when software is available as a package for your distro, it will save you some headaches, and generally be a clean install. Wheras software that is available only as source will work on any distro - but you may have to roll up your sleeves and do some configuration on your own.
Am I close to the mark here?  :-k [/QUOTE]

You hit the bulls eye.

> 
What about software that you install as a package, but you would then like to install a newer version?  I guess in the case of Ubuntu, you can just download the updated package from Ubuntu, right?

Download the updated pacakge from Jdong's backport project...

---

