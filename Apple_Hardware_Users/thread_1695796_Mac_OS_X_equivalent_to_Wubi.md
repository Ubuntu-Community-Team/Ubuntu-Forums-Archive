---
title: "Mac OS X equivalent to Wubi?"
date: 2011-02-26
forum: Apple Hardware Users
---

### Post by Hyperreal_Logic on 2011-02-26
Hello, I'm just curious to know if there exists a Mac OS X equivalent to the Wubi software.  Or something similar that allows you to run Linux next to Mac OS X just like Wubi does on Windows.  I've heard of something called Cooperative Linux, is that similar to Wubi?

---

### Post by AnimeOmega on 2011-02-26
This is not what you're asking for, I don't know of any wubi equivalents for OSX... but maybe you can try this:
 
[http://www.junauza.com/2010/10/installing-ubuntu-1010-on-mac-os-x.html](http://www.junauza.com/2010/10/installing-ubuntu-1010-on-mac-os-x.html)

After you install 'guest additions' you can full screen Ubuntu on top of OSX and it'll behave like the 'real thing' with a little bit of overhead.

---

### Post by s.fox on 2011-02-26
I recall reading that Mubi is "in development" over a year ago (I am unable locate where I have read this), but I have not seen anything emerge.

---

### Post by srs5694 on 2011-02-26
You can create a conventional dual-boot configuration of OS X and Linux on a Mac; however, most of the Ubuntu development effort is geared toward commodity (Windows) PCs, so sometimes things don't work quite as well as they should.

[Cooperative Linux](http://www.colinux.org) ("coLinux" for short) is an interesting technology, but it's more akin to a virtualization tool like [VirtualBox](http://www.virtualbox.org) than to a specialized dual-boot tool like WUBI. CoLinux runs the Linux kernel as a normal process on the host OS, so you can run both OSes simultaneously. AFAIK, coLinux only supports Windows as a host OS at the present time, so it won't really do you much good.

Overall, I recommend either doing a conventional dual-boot installation using any of the several guides that are out there, or running Linux in a VirtualBox or similar virtualization program. The former gives Linux full access to and control of the machine hardware, which is important if you want to use USB devices or something; the latter reduces the risks involved in partitioning and so on, but gives Linux limited access to hardware. Take your pick.

---

