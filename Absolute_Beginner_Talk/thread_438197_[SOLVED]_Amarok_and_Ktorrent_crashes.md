---
title: "[SOLVED] Amarok and Ktorrent crashes"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-05-09
I've had a few problems with both of these apps crashing and giving me a KDE Crash handler - appears to be sim to '3 Little Issues' cam2009 post from 5 days ago - but that's waiting for a post from them

Ktorrent is  the most prone to crashing on my system.

both mine say very similar things on 'front' screen bout causing signal 11 SIGSEV - at least Ktorrent def does as it's on screen at mo and i'm pretty sure Amarok gives same SIGSEV thing!

Don't know how to put the scrollable box into thread so here is the text from the backtrace page - hope that helps (i've removed lots of no debugging symbols found lines hope that helps)

I've been closing crash handler and restarting - not really sure what to do here.

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found) - [COLOR="Red"]originally 34 instances of this[/COLOR]
[Thread debugging using libthread_db enabled]
[New Thread -1235515696 (LWP 6306)]
[New Thread -1253885040 (LWP 6353)]

(no debugging symbols found) - [COLOR="Red"]orginally 42 instances of this[/COLOR]
[KCrash handler]
#6  0xb7e13b9b in dht::ParseRsp () from /usr/lib/libktorrent-2.1.so
#7  0xb7e13dc2 in dht::MakeRPCMsg () from /usr/lib/libktorrent-2.1.so
#8  0xb7e08f21 in dht::RPCServer::readPacket ()
   from /usr/lib/libktorrent-2.1.so
#9  0xb7e09222 in dht::RPCServer::qt_invoke ()
   from /usr/lib/libktorrent-2.1.so
#10 0xb6e4d88b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#11 0xb6e4e330 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#12 0xb75d704c in KNetwork::KClientSocketBase::readyRead ()
   from /usr/lib/libkdecore.so.4
#13 0xb75d7086 in KNetwork::KClientSocketBase::slotReadActivity ()
   from /usr/lib/libkdecore.so.4
#14 0xb75e9143 in KNetwork::KClientSocketBase::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#15 0xb75e91e6 in KNetwork::KDatagramSocket::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#16 0xb6e4d88b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#17 0xb6e4e1a2 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#18 0xb71da877 in QSocketNotifier::activated () from /usr/lib/libqt-mt.so.3
#19 0xb6e7044a in QSocketNotifier::event () from /usr/lib/libqt-mt.so.3
#20 0xb6de4a60 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#21 0xb6de688f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#22 0xb75a8ce2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#23 0xb6d771e9 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#24 0xb6dd6e59 in QEventLoop::activateSocketNotifiers ()
   from /usr/lib/libqt-mt.so.3
#25 0xb6d8bd07 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#26 0xb6dff136 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#27 0xb6dfef46 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#28 0xb6de6609 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#29 0x080653d6 in ?? ()
#30 0xb65feebc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#31 0x08064ec1 in ?? ()

---

### Post by forestpixie on 2007-05-10
"Bump"

---

### Post by orb9220 on 2007-05-10
> Ktorrent is the most prone to crashing on my system.

Do you have the latest 2.1.4? [http://ktorrent.org/](http://ktorrent.org/)

Are you using 64bit or 32bit kernel?
Feisty?

---

### Post by forestpixie on 2007-05-10
Using 2.1 - got it from the Apps - Add/Remove at weekend - looked at ktorrent.org  will try to update ktorrent 

guessing i use the deb package installer 

i appear to be using the latest amarok though


I assume i'm using 32 bit kernel 
still not sure how much to panic about the sigsev thing though

thanks

---

### Post by forestpixie on 2007-05-10
and yes feisty

---

### Post by fabiomb on 2007-06-06
same problem, no clues

---

### Post by forestpixie on 2007-06-07
No problem now after installing new ktorrent version -  both errors apparently sorted.

---

### Post by spiffytech on 2007-06-11
I'm having the same issue with ktorrent. Here's my backtrace in case it helps anyone solve the problem: 

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
[Thread debugging using libthread_db enabled]
[New Thread -1235818800 (LWP 7174)]
[New Thread -1251161200 (LWP 7184)]
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
[KCrash handler]
#6  0xb7dc9bcb in dht::ParseRsp () from /usr/lib/libktorrent-2.1.so
#7  0xb7dc9df2 in dht::MakeRPCMsg () from /usr/lib/libktorrent-2.1.so
#8  0xb7dbef51 in dht::RPCServer::readPacket ()
   from /usr/lib/libktorrent-2.1.so
#9  0xb7dbf252 in dht::RPCServer::qt_invoke ()
   from /usr/lib/libktorrent-2.1.so
#10 0xb6e0388b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#11 0xb6e04330 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#12 0xb758d04c in KNetwork::KClientSocketBase::readyRead ()
   from /usr/lib/libkdecore.so.4
#13 0xb758d086 in KNetwork::KClientSocketBase::slotReadActivity ()
   from /usr/lib/libkdecore.so.4
#14 0xb759f143 in KNetwork::KClientSocketBase::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#15 0xb759f1e6 in KNetwork::KDatagramSocket::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#16 0xb6e0388b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#17 0xb6e041a2 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#18 0xb7190877 in QSocketNotifier::activated () from /usr/lib/libqt-mt.so.3
#19 0xb6e2644a in QSocketNotifier::event () from /usr/lib/libqt-mt.so.3
#20 0xb6d9aa60 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#21 0xb6d9c88f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#22 0xb755ece2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#23 0xb6d2d1e9 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#24 0xb6d8ce59 in QEventLoop::activateSocketNotifiers ()
   from /usr/lib/libqt-mt.so.3
#25 0xb6d41d07 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#26 0xb6db5136 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#27 0xb6db4f46 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#28 0xb6d9c609 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#29 0x080653d6 in ?? ()
#30 0xb65b4ebc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#31 0x08064ec1 in ?? ()

```

---

### Post by bleaked on 2007-06-18
I had been experiencing this same problem with amarok over the past few days.  After searching around I finally found an answer on kubuntuforums.net suggesting that I remove the ~/.xine folder, since it was being corrupted for whatever reason.

So a quick removal of the ~/.xine directory should fix your problem with amarok:
 ```
$ rm -rf ~/.xine
```


As far as KTorrent is concerned, I have no idea and strongly encourage anyone who figures out the instability issues (yes, I'm using the latest beta release) to please let me know.

---

