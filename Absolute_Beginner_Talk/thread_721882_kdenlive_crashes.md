---
title: "kdenlive crashes"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-03-11
Due to problems with the sound on the kdenlive from the repositories, I removed kdenlive, mlt and ffmpeg.  I then downloaded the source packages for all 3 and followed the instructions in the wiki for building kdenlive.  I "turned on" one option which was to disable the new "hybrid" sound in ffmpeg.  Then I followed the rest of the wiki and built ffmpeg, mlt, mlt++ and kdenlive.  Now kdenlive crashes.  Console output is:

kdenlive
kdenlive: //  INIT EFFECT SEARCH
kdenlive: ---------  close 1b
kdenlive: ---------  close 2b
KCrash: Application 'kdenlive' crashing...
dave@dave-desktop:~/kdenlive$ 



Backtrace output is:

Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1234069824 (LWP 18398)]
[KCrash handler]
#6  mlt_properties_set (this=0x0, name=0x8275818 "resource", 
    value=0x84be9a8 "/usr/share/apps/kdenlive/profiles/metadata.properties")
    at mlt_properties.c:277
#7  0xb6ccaa90 in Mlt::Properties::set () from /usr/lib/libmlt++.so.0
#8  0x081aed3b in KRender::KRender ()
#9  0x081af628 in KRenderManager::createRenderer ()
#10 0x081af719 in KRenderManager::findRenderer ()
#11 0x081898d7 in KdenliveDoc::KdenliveDoc ()
#12 0x0817b287 in Gui::KdenliveApp::initDocument ()
#13 0x08183886 in Gui::KdenliveApp::KdenliveApp ()dave@dave-desktop:~/kdenlive$ #14 0x081cd7b5 in main ()


Note that at the front of the traceback "/lib/tls/i686/cmov/libthread_db.so.1" is listed - would this be correct even though I'm just running a PIII-500, or should this library be something along the "i386" line?

Any help would be greatly appreciated!!:)

---

