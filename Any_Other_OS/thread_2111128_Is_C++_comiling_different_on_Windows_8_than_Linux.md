---
title: "Is C++ comiling different on Windows 8 than Linux ?"
date: 2013-02-01
forum: Any Other OS
---

### Post by West201 on 2013-02-01
I'm novice with C++ , and been using Linux (Gentoo/Ubuntu) for a while, and have never used Windows to do any programming. On most Linux Distros it is an easy and simple process. Now I'm thinking of installing Windows 8, would I need to expect anything different ? I read that there is the "MinGW" package for C++, would that be a good alternatives for two users that program on the same computer ? 


Thanks,

---

### Post by meteorrock on 2013-02-01
You could install cygwin to compile your C++ , however its faster and easier to install some sort of hypervisor on your Windows OS and switch over to a linux distro. It will compile on windows fine, it just depends what you are developing. If you are developing something for windo$e, then use cygwin. Cygwin uses a MinGW. 

I use cygwin to port over windo$e apps to linux and vise versa. 

Cygwin has all of the packages to install compilers for C++ however that app is outdated and works better with 32 bit computers.

As the linux kernel is no longer supporting 32 bit compiles, you should think about that. I recommend VMware for a beginners hypervisor. It depends on your computers specs though. It supports file sharing between the host OS and the guest OS.

---

### Post by West201 on 2013-02-01
@ meteorrock

Thank you for your detailed answer. I guess it's too much hassle to just compile on Windows 8, I've heard you can't dual-boot when you have with Window 8, so I guess it's out of the picture. 

Thanks Again !

---

### Post by Grinage on 2013-02-01
I haven't played with Win8 yet, what did MS do to it to make it special so that it wouldn't dual boot or compile correctly

---

### Post by Mark Phelps on 2013-02-01
> **jessejj89 said:**
>  I've heard you can't dual-boot when you have with Window 8

Actually ... yes, you can ... it's just a lot more hassle because preinstalled Win8 PCs nearly always come with UEFI BIOS -- which is very different from the traditional MBR BIOS -- and takes a lot more prep to do the dual-boot properly.

If you're interested in doing that, start a new thread with that as the title -- and someone will come along with directions.

However, what I can tell you in advance is that if you are interested in going that route, make sure you do the following:
1) Use the Backup feature of Win8 to create and burn a Win8 Repair CD.  You will need this later to repair the Win8 boot loader if something goes wrong during the dual-boot setup.
2) Use ONLY the Win8 Disk Management utility to shrink Win8 to make room for Ubuntu.  Do NOT use GParted or the Ubuntu installer to do the shrinkage as that has been known to result in filesystem corruption that will then prevent Win8 from booting.

---

### Post by oldos2er on 2013-02-01
Moved to Other OS/Distro Talk.

---

