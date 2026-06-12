---
title: "Kubuntu 7.10 XServer crashes - where to look for cause?"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by leefw on 2007-11-14
Hi

Since installing Kubuntu 7.10 (fresh install) it seems my Xserver (I think) is crashing for no apparent reason. In other words the whole KDE system just stops, for a split second the console takes over the full screen, some text flickers on the screen (some daemon starting/shutting down it looks like) and I am introduced to the graphical KDE login. When I log on again the desktop appears like it did when I last logged on (not like it was before the crash).

This has happened about 3 times now and I'm not sure of the cause. Maybe I am imagining  things, but it seems to happen when Adept is running on another desktop (I am running 8 desktops). The machine is pretty new, NVidia graphics, running NVidia restriced driver, 64 bit CPU, but I am running i386 version of 7.10. The PC in question is turned off only rarely.

My question is where should I start looking (logs etc) to find the root cause of my problem?

Regards
Lee Francis

---

### Post by Inxsible on 2007-11-14
The common log files are under /var/logs. you can have a look there to look for possible causes.

```
tail -f /var/log/messages

more -f /var/log/messages
```

---

### Post by leefw on 2007-11-14
So "messages" is the file to look at? However, this is what I have since from before the crash (the PC's name is grey):

Nov 14 18:59:01 grey -- MARK --
Nov 14 19:37:01 grey -- MARK --
Nov 14 19:59:01 grey -- MARK --
Nov 14 20:37:01 grey -- MARK --
Nov 14 20:59:01 grey -- MARK --
Nov 14 21:37:01 grey -- MARK --
Nov 14 21:55:35 grey kernel: [12349.988000] NET: Registered protocol family 4
Nov 14 21:55:35 grey kernel: [12350.064000] NET: Registered protocol family 3
Nov 14 21:55:36 grey kernel: [12350.092000] NET: Registered protocol family 5
Nov 14 22:37:01 grey -- MARK --
Nov 14 22:59:01 grey -- MARK --
Nov 14 23:26:56 grey kernel: [17830.224000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/media/video/usbvideo/usbvideo.c: Transfer Statistics: Transferred=0 B Usage=0%
Nov 14 23:59:01 grey -- MARK --
Nov 15 00:37:01 grey -- MARK --

Not much to go on here. The PC crached at about midnight I think, but I'm not 100% sure. Is there any way to turn on log verbosity? Possibly look at a different log file?

---

### Post by leefw on 2007-11-15
So it happened again just now and I noted the time (22.06).

I listed the files in /var/log that had recently changed using ls -ltr and had a look. 

This is what I got. Does this make sense to anyone? I think the last file seems relevant, but doesn't list a cause. 


**/var/log/daemon.log**
```
Nov 15 22:06:11 grey kdm[5910]: X server for display :0 terminated unexpectedly
```

**/var/log/syslog**
```
Nov 15 22:06:11 grey kdm[5910]: X server for display :0 terminated unexpectedly
```

**/var/log/apport.log (last change 22.06)**
```
apport (pid 19249) Thu Nov 15 22:06:10 2007: called for pid 9520, signal 6
apport (pid 19249) Thu Nov 15 22:06:10 2007: executable: /usr/bin/Xorg (command line "/usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-losBfh")
apport (pid 19280) Thu Nov 15 22:06:11 2007: called for pid 9658, signal 11
apport (pid 19280) Thu Nov 15 22:06:11 2007: executable: /usr/bin/artsd (command line "/usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -c drkonqi -l 3 -f")
modinfo: could not open cdrom: No such device
modinfo: could not open cdrom: No such device
apport (pid 19280) Thu Nov 15 22:06:16 2007: wrote report /var/crash/_usr_bin_artsd.1000.crash
```


**/var/log/kdm.log (last change 22.06)**
```
SetGrabKeysState - enabled

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c9581]
1: [0xffffe420]
2: /usr/bin/X [0x817e39d]
3: /usr/bin/X [0x817a9ef]
4: /usr/bin/X(CompositeGlyphs+0x9a) [0x816129a]
5: /usr/bin/X [0x8168f19]
6: /usr/bin/X [0x8164315]
7: /usr/bin/X [0x815754e]
8: /usr/bin/X(Dispatch+0x1aa) [0x808f47a]
9: /usr/bin/X(main+0x495) [0x8076f05]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d91050]
11: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 11.  Server aborting


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux grey 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 15 22:06:11 2007
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
```

Any ideas?

---

### Post by leefw on 2007-12-26
It seems that this always happens when Adept is running. It has never happened when Adept is not running. I am pretty sure this program is the culprit. However, X crashes and restarts as if nothing has happened. No error message is reported and no "report your KDE bug" dialog box appears. I never had any Adept problems with Dapper, Edgy or Feisty.

Isn't there any way I can turn on debug logging for Adept or X server to collaborate my assumption?

---

