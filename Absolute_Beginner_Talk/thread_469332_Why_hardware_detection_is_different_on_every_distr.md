---
title: "Why hardware detection is different on every distro?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by sicofante on 2007-06-09
Since almost everything is opensourced in the Linux world, why isn't hardware detection in every distro as good as it is in the better distro?

I mean, this is not a preferences issue, like Gnome vs KDE or Brasero vs K3B. It's just the distro detects the hardware correctly or it doesn't.

Shouldn't all hardware detection success stories lead to a unified repository or something similar? Shouldn't hardware be detected just by "Linux" instead of "by distro X"? What's the benefit of choice here? 

I don't get it.

Just my curiosity.

---

### Post by Bachstelze on 2007-06-09
> **sicofante said:**
> Since almost everything is opensourced in the Linux world, why isn't hardware detection in every distro as good as it is in the better distro?

The principal thing regarding hardware detection is the kernel. The official source of the Linux kernel is [http://kernel.org](http://kernel.org). A kernel taken straight from kernel.org and unmodified is called a *"vanilla"* kernel. But most distros do *not* use a vanilla kernel. For example, in the kernel they ship with Ubuntu, Ubuntu developpers add some drivers that are not included in the vanilla kernel, with the result that Ubuntu will detect some hardware "out of the box" that other distros will not.

Keep in mind, though, that the "core" of the kernel is still the same, and that because a driver is not shipped with your kernel does not mean you can't install it later. In 90% of the cases, if a piece of hardware works in *one* distro, it will be possible to make it work in *all* the distros.


Oh, and byt he way, there is no better, only different :)

---

### Post by ThinkBuntu on 2007-06-09
With a normal, up-to-date kernel, all hardware in fact IS detected. The differences you notice are due to developer decisions regarding which drivers and services to include, offer from repositories, and to load. Ubuntu has good detection because it includes and loads the kitchen sink by default. Really, every distro from Arch to Gentoo to Ubuntu to Zenwalk can be made to detect hardware equally, with different degrees of effort. The tradeoff is often speed, specifically with the boot.

---

### Post by az on 2007-06-09
> **sicofante said:**
> Since almost everything is opensourced in the Linux world, why isn't hardware detection in every distro as good as it is in the better distro?

Because there are different projects and different versions of projects that work with each other.

How do you know when to include a particular driver in your distro?  If you waited for it to mature and become part of the mainstream kernel, it could take months or years.  If you include it right away (release early, release often) you risk upsetting users who think the hardware should work, but it really is too buggy to work for everybody.

The rule of thumb is the community around the project.  If the community is active and seems to be able to sustain the project, it will generally develop faster.  Including this in your distro may actually help the project gain community members.

There have been many cases in the past where some distros tried to support too much, and basically constantly had a buggy, unstable kernel (Think Mandrake linux in 2000-2005)


> **sicofante said:**
> 
I mean, this is not a preferences issue, like Gnome vs KDE or Brasero vs K3B. It's just the distro detects the hardware correctly or it doesn't.

Well, how long did it take for everybody to switch from kernel devices to Udev and HAL?  Warty still used hotplug when it first came out.  Not to mention that hardware support is a moving target.  It is not always easy to make the whole stack support both old and new hardware at the same time.

Come to think of it, it's pretty impressive as it is.


> **sicofante said:**
> 
Shouldn't all hardware detection success stories lead to a unified repository or something similar? Shouldn't hardware be detected just by "Linux" instead of "by distro X"? What's the benefit of choice here? 

I don't get it.

Just my curiosity.

It's not that simple.  What do yo do if one driver conflicts with another?  What do you do when you want to improve the infrastructure and clean up the way the kernel handles messages, but this breaks some drivers until the authors of those drivers figure out what the problem it?  The kernel needs to evolve, you know.  The whole stack does.

---

### Post by az on 2007-06-09
> **ThinkBuntu said:**
> The differences you notice are due to developer decisions regarding which drivers and services to include, offer from repositories, and to load. Ubuntu has good detection because it includes and loads the kitchen sink by default. .... The tradeoff is often speed, specifically with the boot.

No.  The Ubuntu kernel detects and loads modules on-demand.  There are very few modules that get loaded for nothing.  Their impact on speed is insignificant.

In the olde days of linux, when you would pretty much need to compile a kernel which was specific to your particular hardware, the kernel that shipped with your distro would include a lot of drivers built-in, so that it could actually boot and install the system for you.  Ever since distros started shipping a kernel with an initrd (ram disk) which autodetects modules at a boot time, this has not been necessary.

---

### Post by ThinkBuntu on 2007-06-09
> **az said:**
> No.  The Ubuntu kernel detects and loads modules on-demand.  There are very few modules that get loaded for nothing.  Their impact on speed is insignificant.

In the olde days of linux, when you would pretty much need to compile a kernel which was specific to your particular hardware, the kernel that shipped with your distro would include a lot of drivers built-in, so that it could actually boot and install the system for you.  Ever since distros started shipping a kernel with an initrd (ram disk) which autodetects modules at a boot time, this has not been necessary.
That's nonsense. It's a well-known fact that Ubuntu loads more modules than are necessary. For example, how else can you explain it loading Bluetooth when my computer doesn't have any Bluetooth devices? I've heard of it also automatically loading Wacom tools, etc.

---

### Post by az on 2007-06-10
> **ThinkBuntu said:**
> That's nonsense. It's a well-known fact that Ubuntu loads more modules than are necessary. For example, how else can you explain it loading Bluetooth when my computer doesn't have any Bluetooth devices? I've heard of it also automatically loading Wacom tools, etc.

Just run 
lsmod
and see.

It's a well know fact, eh?  I think you should familiarize yourself with how the kernel works before we continue this conversation.

---

