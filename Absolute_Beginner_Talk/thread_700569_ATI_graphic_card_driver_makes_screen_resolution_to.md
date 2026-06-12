---
title: "ATI graphic card driver makes screen resolution to 800x600 and it should be 1280x1024"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by K0ivu on 2008-02-18
Hi,

I have a His Excalibur Radeon 9600 128MB graphic card, and a 19' ViewSonic VA903b tft-monitor.
I am using Ubuntu 7.10 Gutsy.

Ubuntu works fine with the resolution 1280x1024, but when I install the drivers, only possible resolutions are 800x600 and 640x480. So how can I make the screen resolution to 1280x1024 and have the graphic card driver enabled at the same time?

What I have tried so far:
1. I installed the drivers through System/Administration/Restricted Drivers Manager
--> didn't work --> I uninstalled the driver
2. I installed the driver through terminal
--> didn't work --> I uninstalled the driver
3. I installed the drivers using Envy
--> didn't work --> I uninstalled the driver and Envy

Every time I installed the drivers and rebooted the system, a high resolution (=1280x1024) Ubuntu loading screen is displayed, but after that there comes this low resolution graphical screen which tells me that Ubuntu is running on a low resolution mode. I can change the graphic card- and monitor-settings from there. 
The graphic card is correct there, and the monitor is set to plug'n'play monitor with resolution 640x400. 
If I change the monitor to generic 19' tft- monitor and change the resolution to 1280x1024 and press the test button, everything seems to work. Then I press the ok-button and Ubuntu starts with resolution 640x480. 
The only way I can get the high resolution back, is to disable the graphics card driver and reboot. Without the graphics card driver Ubuntu starts automatically with resolution 1280x1024.

Any ideas?

---

### Post by petersonjacob on 2008-02-18
go to applications -> system tools -> and click on your dedicated card software that should have come with the driver, hopefully it is similar to nvidia's

---

### Post by petersonjacob on 2008-02-18
whoa i read it wrong sorry
try this
dpkg-reconfigure xserver-xorg
as root
adn choose the ati driver, it should be on the list somewhere look
then dont change anything else just keep hitting enter and selecting the default until the prompt comes back, then type
reboot
hope it helps

ps use envy i know you did it once, but do it again, its extremely useful

---

### Post by spiderbatdad on 2008-02-18
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Zimmer on 2008-02-18
[http://ubuntuforums.org/showthread.php?t=276650](http://ubuntuforums.org/showthread.php?t=276650)

Have a look at post #3 and check out your monitor's capabilities from the xorg.log file.

Then create a custom modeline and mode statement for the xorg.conf as described in that post.

---

### Post by K0ivu on 2008-02-19
Ok, I tried to install the drivers via terminal once again, and after typing following command, the xorg.conf disappears.
> sudo aticonfig --initial

Here is the terminal output:
> 
tuomo@tuomo-ubuntu-gutsy:~$ sudo depmod -a
tuomo@tuomo-ubuntu-gutsy:~$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-2
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfcee9d2 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7dbb92b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7d64050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:01 18171143   /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:01 18171143   /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7d40000-b7d41000 rw-p b7d40000 00:00 0 
b7d41000-b7d43000 r-xp 00000000 08:01 13829070   /lib/tls/i686/cmov/libdl-2.6.1.so
b7d43000-b7d45000 rw-p 00001000 08:01 13829070   /lib/tls/i686/cmov/libdl-2.6.1.so
b7d45000-b7d49000 r-xp 00000000 08:01 18171187   /usr/lib/libXdmcp.so.6.0.0
b7d49000-b7d4a000 rw-p 00003000 08:01 18171187   /usr/lib/libXdmcp.so.6.0.0
b7d4a000-b7d4c000 r-xp 00000000 08:01 18171176   /usr/lib/libXau.so.6.0.0
b7d4c000-b7d4d000 rw-p 00001000 08:01 18171176   /usr/lib/libXau.so.6.0.0
b7d4d000-b7d4e000 rw-p b7d4d000 00:00 0 
b7d4e000-b7e92000 r-xp 00000000 08:01 13829067   /lib/tls/i686/cmov/libc-2.6.1.so
b7e92000-b7e93000 r--p 00143000 08:01 13829067   /lib/tls/i686/cmov/libc-2.6.1.so
b7e93000-b7e95000 rw-p 00144000 08:01 13829067   /lib/tls/i686/cmov/libc-2.6.1.so
b7e95000-b7e98000 rw-p b7e95000 00:00 0 
b7e98000-b7ebb000 r-xp 00000000 08:01 13829071   /lib/tls/i686/cmov/libm-2.6.1.so
b7ebb000-b7ebd000 rw-p 00023000 08:01 13829071   /lib/tls/i686/cmov/libm-2.6.1.so
b7ebd000-b7faa000 r-xp 00000000 08:01 18171170   /usr/lib/libX11.so.6.2.0
b7faa000-b7fae000 rw-p 000ed000 08:01 18171170   /usr/lib/libX11.so.6.2.0
b7fae000-b7fbb000 r-xp 00000000 08:01 18171191   /usr/lib/libXext.so.6.4.0
b7fbb000-b7fbc000 rw-p 0000d000 08:01 18171191   /usr/lib/libXext.so.6.4.0
b7fbc000-b7fc3000 r-xp 00000000 08:01 18171213   /usr/lib/libXrender.so.1.3.0
b7fc3000-b7fc4000 rw-p 00006000 08:01 18171213   /usr/lib/libXrender.so.1.3.0
b7fc4000-b7fc9000 r-xp 00000000 08:01 18171211   /usr/lib/libXrandr.so.2.1.0
b7fc9000-b7fca000 rw-p 00005000 08:01 18171211   /usr/lib/libXrandr.so.2.1.0
b7fca000-b7fcb000 rw-p b7fca000 00:00 0 
b7fcb000-b7fd5000 r-xp 00000000 08:01 13795395   /lib/libgcc_s.so.1
b7fd5000-b7fd6000 rw-p 0000a000 08:01 13795395   /lib/libgcc_s.so.1
b7fd6000-b7fd8000 rw-p b7fd6000 00:00 0 
b7fd8000-b7ff2000 r-xp 00000000 08:01 13795341   /lib/ld-2.6.1.so
b7ff2000-b7ff4000 rw-p 00019000 08:01 13795341   /lib/ld-2.6.1.so
bfcda000-bfcef000 rw-p bfcda000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
tuomo@tuomo-ubuntu-gutsy:~$ 


Edit: Considering the amount xorg.conf backup-files, this has propably happened every time I've tried to install the drivers.

---

### Post by spiderbatdad on 2008-02-19
sudo aticonfig --initial --input=/etc/X11/xorg.conf

---

### Post by K0ivu on 2008-02-19
> **spiderbatdad said:**
> sudo aticonfig --initial --input=/etc/X11/xorg.conf
I tried it.
It did not change anything. Exactly the same terminal output as with 'sudo aticonfig --initial'.

Only difference were the memory/register addresses, like 0xbfcee9d2 (or whatever they are)..

---

