---
title: "XServer crashing Live CD...no ATI or NVIDIA"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by lebowski419 on 2007-04-22
Hi, I am having trouble booting the Live CD for Feisty on my laptop as the X Server crashes every time.  I would eventually like to install Feisty in a dual-boot set-up, but if I can't get the video working, I don't see the point.  Anyway, my laptop's specs are:

Dell Inspiron 5160
Pentium 4 (Mobile) 2.8 mHz
512 MB RAM
XGI Volaris-XP5 32 MB

And the message I get relating to the crash is:

> 
XWindow System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubunut 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
           Before reporting problems, check [http://wikix.org](http://wikix.org)
           to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
             (++) from command line, (!!) notice, (II) informational,
             (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log File: "/var/long/Xorg.0.log", Time: Sun Apr 22 20:35:25 2007
(==) Using config file: "etc/X11/xorg.conf"

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/bin/X11/X(InitOutput+0x9aa) [0x80a5b9a]
3: /usr/bin/X11/X(main+0x27b) [0x807456b]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d2febc]
5: /usr/bin/X11/X(FontFileCompleteXLFD+0x1e1) [0x9073ab1]

Fatal server error:
Caught signal 11.  Server aborting

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
         after 0 requests (0 known processed) with 0 events remaining.


---

### Post by leibowitz on 2007-04-22
That's probably an huge big problem. That's the first time I see an Xorg crashing like that.

Can you try to start some commands when you are at the prompt. 

> (==) Log File: "/var/log/Xorg.0.log", Time: Sun Apr 22 20:35:25 2007
(==) Using config file: "/etc/X11/xorg.conf"

Please try to join the **/var/log/Xorg.0.log** file in here. It would be intersting to know what it does.

Also I suspect it's your XGI graphic card combined with your monitor that does this.

Are you able to try with another monitor. If yes, please report the results in here aswell.

---

