---
title: "Help playing DVD, strange problem :S"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by JoeCan on 2007-04-02
Ok, so this is a new Ubuntu setup and I installed Kde last night. I tried to play a DVD with Kaffeine and it said it needed codecs to work. So, I downloaded all of the necessary codecs that I needed and now Kaffeine crashes when trying to read the DVD. It gives me a signal 7 error. 

I tried the same thing in GNOME...the program (and any other DVD program) now says either I don't have proper rights or the DVD has no data. I know the disc has data on it as I can read the individual files through my computer's drive. So, maybe I don't have rights? How would I run Kaffeine or another program as SU...and, why would I have to/want to?

I have no idea where the problem lies? I'm pretty good at software and hardware issues but I'm new to Linux and have tried everything I can think of. Can someone give me any suggestions on what the problem might be? Thanks so much in advance, -Joe



This is the output of the debug:

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1237903696 (LWP 6942)]
[New Thread -1332941920 (LWP 6960)]
[New Thread -1317086304 (LWP 6957)]
[New Thread -1308693600 (LWP 6956)]
[New Thread -1300100192 (LWP 6955)]
[New Thread -1289819232 (LWP 6954)]
[New Thread -1277326432 (LWP 6951)]
[New Thread -1268663392 (LWP 6950)]
[New Thread -1260270688 (LWP 6947)]
[New Thread -1247458400 (LWP 6946)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0 0xffffe410 in __kernel_vsyscall ()
#1 0xb66173fb in __read_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2 0xb711797e in _kde_IceTransGetConnectionNumber ()
from /usr/lib/libDCOP.so.4
#3 0xb711762f in _kde_IceTransRead () from /usr/lib/libDCOP.so.4
#4 0xb71114af in _kde_IceRead () from /usr/lib/libDCOP.so.4
#5 0xb7115c9f in KDE_IceProcessMessages () from /usr/lib/libDCOP.so.4
#6 0xb71013f9 in DCOPClient::callInternal () from /usr/lib/libDCOP.so.4
#7 0xb71016dd in DCOPClient::callInternal () from /usr/lib/libDCOP.so.4
#8 0xb7106127 in DCOPClient::call () from /usr/lib/libDCOP.so.4
#9 0xb7106187 in DCOPClient::call () from /usr/lib/libDCOP.so.4
#10 0xb7106388 in DCOPClient::disconnectDCOPSignal ()
from /usr/lib/libDCOP.so.4
#11 0xb7106cf9 in DCOPObject::~DCOPObject () from /usr/lib/libDCOP.so.4
#12 0xb781538a in KDirListerCache::~KDirListerCache ()
from /usr/lib/libkio.so.4
#13 0xb78092f4 in KServiceTypeProfile::clear () from /usr/lib/libkio.so.4
#14 0xb63cd54f in __cxa_finalize () from /lib/tls/i686/cmov/libc.so.6
#15 0xb774ed03 in ?? () from /usr/lib/libkio.so.4
#16 0xb7998120 in ?? () from /usr/lib/libkio.so.4
#17 0xb79931fc in ?? () from /usr/lib/libkio.so.4
#18 0xbfad00b8 in ?? ()
#19 0xb795630c in _fini () from /usr/lib/libkio.so.4
#20 0xb795630c in _fini () from /usr/lib/libkio.so.4
#21 0xb7f9f4ce in _dl_rtld_di_serinfo () from /lib/ld-linux.so.2
#22 0xb63cd299 in exit () from /lib/tls/i686/cmov/libc.so.6
#23 0xb6aa8142 in QApplication:11_initialize_style ()
from /usr/lib/libqt-mt.so.3
#24 0xb71ec9cd in KApplication:ioErrhandler () from /usr/lib/libkdecore.so.4
#25 0xb71eca19 in KApplication:ioErrhandler () from /usr/lib/libkdecore.so.4
#26 0xb667bf4d in _XIOError () from /usr/lib/libX11.so.6
#27 0xb667d817 in _XSend () from /usr/lib/libX11.so.6
#28 0xb667e7b0 in _XEventsQueued () from /usr/lib/libX11.so.6
#29 0xb666a262 in XPending () from /usr/lib/libX11.so.6
#30 0xb6ac8360 in QEventLoop::ProcessEvents () from /usr/lib/libqt-mt.so.3
#31 0xb6b3c25e in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#32 0xb6b3c06e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#33 0xb6b23731 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#34 0x08072a05 in ?? ()
#35 0xb63b68cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#36 0x080725f1 in ?? ()
```

---

### Post by crispy_420 on 2007-04-02
I have not used kaffeine as I like VLC for DVD playback. But try installing kaffeine-xine to handle DVD playback.

---

### Post by JoeCan on 2007-04-02
Thanks for the help.  I tried downloading that package as well as all of the VLC packages.  In GNOME, VLC gives me the "either you don't have proper rights or the DVD has no data" error as other DVD players.  In Kde the same programs just crash.  Any other ideas?  I have no idea.  It could be some kind of copy protection I guess but it's not a special DVD or anything.  I'm at work at the moment so I haven't tried any other DVDs (since it's my laptop).

---

### Post by zvacet on 2007-04-03
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

I think this can help you.

---

### Post by russell.h on 2007-04-03
What DVD is it? If it has region protection or some sort of encryption (copy protection) it might give you trouble, although I thought VLC could handle most of that stuff.

---

### Post by johnny4north on 2007-04-03
maybe the media players default setting DVD://  does not match you ubuntu's.  mine is dvd://, but other have been different.  click on file.then browse.  find dvd, then click open

---

### Post by kahrytan on 2007-04-03
To play commercial dvds, you need the Libdvdcss2 and libdvdread3. The easiest method is just use Easy Ubuntu.

Just install the w322codecs. And use VLC to play the dvd. VLC won't show the menu. It will just play the movie.

---

### Post by crispy_420 on 2007-04-03
VLC does show menus. In fact it is an option, "DVD (menus)", under open disc. You do miss all previews though.

If you tried all the required software (libdvdcss, libdvdread, etc.) and still no luck, my guess would be permissions. Are you running as primary user?

---

### Post by Kohbo on 2007-04-08
it worked for me. Also enabled all my other media types which I was trying to figure out. thanx a bunch

---

### Post by Mets on 2007-04-09
> **crispy_420 said:**
> you do miss all previews though.
Oh man, no previews?  What a loss hehe :popcorn:

---

