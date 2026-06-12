---
title: "Building IEEE subsystem"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by sullust on 2006-04-20
Hi all,

I am a newbie to linux and was hoping to get some help here. I bought a new Acer 8200 Travelmate lappy, which is great except that kubuntu has no drivers for any of the hardware.

When I first installed linux, it coundn't display to my monitor, it was scrolling issues about ACPI battery issues, and it couldn't find either my LAN ethernet card nor my wireless one.

I managed to fix the first two issues by combing the forums, but i cannot find any answer/have not been able to figure out how to get either of my lan cards connected.

I am trying my wlan card first (haven't been able to find a lan driver for linux from intel). I tried the ndiswrapper method for loading my windows driver, but although it loads correctly, I cannot find it on any kde network tool.

So I am trying to install the native driver. In order to do this, I apperently need to install the ieee subsystem. I did so and tried to build it.

This is what I got:
:~/installs/ieee80211-1.1.13$ make
Checking in /lib/modules/2.6.12-9-386 for ieee80211 components...
grep: /lib/modules/2.6.12-9-386/build//.config: No such file or directory
grep: /lib/modules/2.6.12-9-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.12-9-386/build M=/home/dpoland/installs/ieee80211-1.1.13 modules
make[1]: Entering directory `/lib/modules/2.6.12-9-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-9-386/build'
make: *** [modules] Error 2

I do not know how to fix this. The doco just says that i need to build it for my kernel, but I thought thatts what the 'make' command did!

What am I missing?

Thanks!

---

### Post by Ensnared on 2006-04-20
You probably just need the header-files for your running kernel. This is a stripped down version of the source-tree of the kernel you're running, which containes files needed to compile drivers and such that need certain information from the source of the current running kernel.

Don't know if that made any sense, but here's what you do:```
sudo apt-get install linux-headers-$(uname -r)
```
This will install the necessary package to compile drivers for your running kernel. Once it's installed, try running make in the iee80211-directory again.

---

### Post by sullust on 2006-04-22
Thanks Ensnared,

I did that and I definately got further. It prompted me to update some configuration files and I said yes. Now it's giving me more errors:

[FONT="Courier New"]dpoland@DPOLAND-ACER: ~/installs/ieee80211-1.1.13dpoland@DPOLAND-ACER:~/installs/ieee80211-1.1.13$ make
Checking in /lib/modules/2.6.12-9-386 for ieee80211 components...
make -C /lib/modules/2.6.12-9-386/build M=/home/dpoland/installs/ieee80211-1.1.13 modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/dpoland/installs/ieee80211-1.1.13/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/dpoland/installs/ieee80211-1.1.13/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/dpoland/installs/ieee80211-1.1.13] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [modules] Error 2[/FONT]

I installed the gcc-4.0 package, but it keeps repeating the same error. Wouldn't the gcc-4.0 package have the same utilities as the gcc3.4 package? Ubuntu came with versions 3.3 and 4.0 of gcc. sould i uninstall 4.0 and install 3.4? would this fix the problem?

Thanks!

---

### Post by Ensnared on 2006-04-22
The problem here is that your kernel was compiled with gcc-3.4, which means modules also needs to be compiled with that version. I've no idea if forcing it to compile with gcc-4.x will work, so I reccomend that you simply install gcc-3.4 ;)```
sudo apt-get install gcc-3.4
```
Don't uninstall your other versions, they can all coexist nicely. I don't really know why the kernel is compiled with gcc-3.4 instead of 4.0, but I'm sure there's a reason for it. I've compiled my own kernel using gcc-4.0 though and haven't had any problems so far.

---

