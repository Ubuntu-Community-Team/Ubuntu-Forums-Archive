---
title: "BSD Music Editor?"
date: 2006-09-11
forum: BSD
---

### Post by Scheater5 on 2006-09-11
Alright, I know there's been discussion about "not comparing open source software to commercial software because it's coded by individuals" - but allow a noob this question:
I can't find a music notation program suitable to my needs on Linux, but is there maychance one on BSD that anyone knows of?
I know it's asking alot to compare open source software to the likes of Finale, but I really need something along those lines.  I'm a college music major, and a powerful music notation program really is a must.  It's just one more thing tieing me to Windows at the moment.  Rosegarden and Lillypond just don't cut it.  I'd just use Powertabs and Finale in a virtual machine, but VMware doesn't include midi support.  So, does anyone know of another program - in BSD or in any open source system.  At the moment I don't even have BSD, but I'd put it alongside Ubuntu in this system for that sole purpose if Ifound a good program.

---

### Post by christhemonkey on 2006-09-11
Something like Noteedit?
[http://noteedit.berlios.de/](http://noteedit.berlios.de/)

Or musescore?
[http://mscore.sourceforge.net/](http://mscore.sourceforge.net/)


Oh an they are both for linux, and use qt toolkit (kde one)
Noteedit is in the repos, but mscore isnt.

---

### Post by Lord Illidan on 2006-09-11
I don't think so. BSD is even more obscure than Linux...and also, it uses many linux apps..like KDE, firefox, etc.

Why not try wine to run the windows versions under linux?

---

### Post by Scheater5 on 2006-09-11
Even wine is over my head at the moment, and while I'm willing to put forth effort to get many things to work in Linux, a music editor is something I need to "just work" - at least for the time being.  Should something go wrong it would affect my grade - not an acceptable risk for me now.

---

### Post by christhemonkey on 2006-09-11
And finale seems to run reasonably under wine:
[http://appdb.winehq.org/appview.php?iAppId=454](http://appdb.winehq.org/appview.php?iAppId=454)

To install noteedit:
```
sudo apt-get install noteedit 
```
It will probably pull, loooads of dependencies, but hopefully, all will be well.

---

### Post by Lord Illidan on 2006-09-11
Then if it is that important, dual boot..

---

### Post by Scheater5 on 2006-09-11
It is important - and for the time being I am dual booting (actually, I'm running Windows on another computer, although it *is* installed on this one, I just despise having to dual boot) but like I said, it's just one more thing tieing me to Windows.  And it's pretty much the only important one - I can live without my games, but I've gotta do my homework!  
O, and Noteedit crashes every time I try to open it - don't have time to post details, but I'll get back to you ASAP - thanx again guys, because Noteedit looks to be exactly what I need.

---

### Post by mips on 2006-09-12
Look at this thread and follow the links,  [http://www.ubuntuforums.org/showthread.php?t=252280](http://www.ubuntuforums.org/showthread.php?t=252280)

Also do a search here for 'lilypond' and you will find many music notation related threads, not only on lilypond.

---

### Post by Scheater5 on 2006-09-13
"Short Description
The application NoteEdit (noteedit) crashed and caused the signal 6 (SIGABRT)"

The KDE crash handler comes up with this message every time I try to run NoteEdit - I've tried uninstalling and reinstalling to no avail.  Anyone have any ideas?

edit: this has come up on the forums before, and no one had an answer

---

### Post by Scheater5 on 2006-09-14
> (no debugging symbols found)
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
[Thread debugging using libthread_db enabled]
[New Thread -1236653216 (LWP 8243)]
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
#6  0xffffe410 in __kernel_vsyscall ()
#7  0xb7bd39a1 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb7bd52b9 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7db1c84 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#10 0xb7daf915 in __gxx_personality_v0 () from /usr/lib/libstdc++.so.6
#11 0xb7daf94a in std::terminate () from /usr/lib/libstdc++.so.6
#12 0xb7dafa7e in __cxa_throw () from /usr/lib/libstdc++.so.6
#13 0xb6b6b2e7 in TSE3::MidiSchedulerFactory::createScheduler ()
   from /usr/lib/libtse3-0.3.1.so
#14 0xb7ed2ce1 in NMidiMapper::NMidiMapper ()
   from /usr/lib/noteedit/libnoteedit.so.1
#15 0x0804a399 in ?? ()
#16 0x081a6630 in ?? ()
#17 0x0804ac9e in vtable for QGList ()
#18 0x00000001 in ?? ()
#19 0xb76bcd70 in QColor::color_init () from /usr/lib/libqt-mt.so.3
#20 0x00000000 in ?? ()

This is what the backtrace yields - I really can't interpret it.  If someone could help me, it'd be much appreciated - if someone could help me to interpret it myself I'd be even happier so I can fix it myself in the future.

---

