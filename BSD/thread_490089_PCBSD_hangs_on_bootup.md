---
title: "PCBSD hangs on bootup"
date: 2007-07-02
forum: BSD
---

### Post by Scheater5 on 2007-07-02
There seems to be alot of these problems over as the pcbsd forums, but none of them seem to have the exact problem I have.  
I installed PCBSD over a windows install, and after reboot it hangs on bootup.  Booting verbose shows it hangs right after the login prompt, which I'm assuming means X is failing.  I have no knowledge of any way to alter my setup or access a terminal in BSD.  Safe mode and the ACPI override yield no results.  Thought I'd post in here with people I'm familiar with before I go to a BSD forum.  Anyone have any ideas?

---

### Post by theonlyrealperson on 2007-07-03
I had a similar problem, and although I don't know how to fix yours - it may be related to my problem:

I installed PCBSD to my laptop three times. Each time, the PCBSD system failed to create a user, so I had nothing to log into. I fixed it by ctrl-alt-backspacing out of X and adding the user again.

Possibly related, I don't know. Try getting out of X and adding a user.

---

### Post by Scheater5 on 2007-07-03
I'd give that a shot, except for two things:
I tried  installing a couple times, one with automatic login turned on and another with it turned off.
And ctrl+alt+backspace apparently does nothing.
I guess I'll boot in single user mode and add a user and see if it helps.  But if I understand it right, that's unrelated to my problem.  Thanks anyway.

---

### Post by Scheater5 on 2007-07-03
I can't get any access to my BSD install.  Ctrl+alt+backspace does nothing, nor does the linux commands for accessing a terminal (ctrl+alt+F* ), or escape or the numeral keys or enter or any random punch of keys I can come up with yields any apparent results after the hang.  Booting under "single user mode" gives me access to a terminal, but no write access, so adduser is basically useless.  
I really wanted the .pbi software install - I hate "ports."  Compiling everything is the reason I don't use Sabayon anymore or have tried Gentoo.  I'm new to BSD and I've read some things that imply there is a collection of software binaries (the frequent use of "third party software" in relation to the ports system says to me that officially supported software is supplied in binary).  But since I can't seem to get PC-BSD to work I'm going to try DesktopBSD, even if it is without the pbi binaries.  Let you guys know how it goes.

---

### Post by theonlyrealperson on 2007-07-04
Well, here's a place I can help you then ;)

Use the package system. This ftp site seems to have programs that are more updated than using the "pkg_add -r" option. 

[ftp://ftp.freebsd.org/pub/FreeBSD/ports/i386/packages-current/All/]("ftp://ftp.freebsd.org/pub/FreeBSD/ports/i386/packages-current/All/")

Good luck!

---

### Post by Protostar on 2007-07-08
> **Scheater5 said:**
> I can't get any access to my BSD install.  Ctrl+alt+backspace does nothing, nor does the linux commands for accessing a terminal (ctrl+alt+F* ), or escape or the numeral keys or enter or any random punch of keys I can come up with yields any apparent results after the hang.  Booting under "single user mode" gives me access to a terminal, but no write access, so adduser is basically useless.  
I really wanted the .pbi software install - I hate "ports."  Compiling everything is the reason I don't use Sabayon anymore or have tried Gentoo.  I'm new to BSD and I've read some things that imply there is a collection of software binaries (the frequent use of "third party software" in relation to the ports system says to me that officially supported software is supplied in binary).  But since I can't seem to get PC-BSD to work I'm going to try DesktopBSD, even if it is without the pbi binaries.  Let you guys know how it goes.


I really like FBSD, and as soon as I get the funds to buy another cheap box thats whats going on it. The ports are a great system of installing software and I wish other Linux distros would emulate it. The problem is that you only use ports for small or moderately sized software. You don't build a software package(s) like Xorg or KDE from ports unless abosutely necessary, because depending upon the speed of your machine and internet connection, this could take anywhere from several hours to a couple days. In fact this was the reason that brought me back to Kubuntu on this machine as the ridiculously long time it took to update to Xorg 7.2 and on top of that it was updating all of KDE as well. After about 7 hours of compiling nonstop I just killed the updating process and wiped the entire installation with Kubuntu.

---

### Post by Protostar on 2007-07-08
I also encountered a hangup problem with PC-BSD as well, which was the reason I went with vanilla FBSD.  It wouldn't even get to the login prompt, when a kernel panic message would appear saying something to the effect the allocation of virtual memory filesystem had failed or something like that.

---

