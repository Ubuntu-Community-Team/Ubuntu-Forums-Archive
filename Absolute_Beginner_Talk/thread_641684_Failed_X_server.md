---
title: "Failed X server"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by loki233 on 2007-12-15
I recently installed Ubuntu Studio via Wubi on my HP dv6000 laptop. The install went fine, but when I try to boot into Ubuntu, I get a message that says:

"Failed to start the X server (your graphical 
interface).  It is likely that it is not set 
up correctly.  Would you like to view the X 
server output to diagnose the problem?"

I select "yes" and get this:


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Versio n11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-15-lowlatency #2 SMP
PREEMPT Sun Apr 15 07:39:03 UTC 2007 i686
Build Date: 04 April 2007
                Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
                to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
               (++) from command line, (!!) notice, (II) informational,
               (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 15 17:17:59 2007
(==) Using config file: "/etc/X11/xorg.conf"

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/bin/X(InitOutput+0x9aa) [0x80a5b9a]
3: /usr/bin/X(main+0x27b) [0x807456b]
4: /lib/tls/i686/comov/libc.so.6(__libc_start_main+0xdc) [0xb7d08ebc]
5: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error: 
Caught signal 11. Server aborting


I don't know what any of this means, or how to fix the problem. I tried to install Ubuntu Studio the same way a few months ago and the same thing happened.

---

### Post by jken146 on 2007-12-15
OK, you probably just need to reconfigure your X settings.  First, hit Ctrl+Alt+F1 to get a terminal, then type ```
sudo dpkg-reconfigure xserver-xorg
``` and go through the setup process.  After that, reboot/restart X and you should have your GUI back.  Good luck!

---

### Post by loki233 on 2007-12-15
It asks me for my X server driver, and I don't know what that means.  My videocard is an intgrated Intel 945GM...

---

### Post by loki233 on 2007-12-15
And I also don't know how to restart X.

---

### Post by PinkFloyd102489 on 2007-12-15
sudo /etc/init.d/xorg-server restart


That should kill and load the X server.

---

