---
title: "Could not find mkspecs for your QMAKESPEC after trying:/usr/share/qt//mkspec"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by JudasReanimated on 2007-07-28
Trying to install QDVD Author and I keep getting this error. 

[B]"Could not find mkspecs for your QMAKESPEC after trying:
        /usr/share/qt//mkspecs
Error processing project file: configurator.pro
make: *** No targets specified and no makefile found.  Stop.
Problems compiling configurator application
Please report to [email]qdvdauthor@users.sf.net[/email]"[/B]

Any ideas on what to do? 
So far google has either failed me, or confused me.

---

### Post by JudasReanimated on 2007-07-29
Anyone?

---

### Post by Hendrixski on 2007-08-01
Yeah, I'm having problems with not locating qmakespec. it seems that Qt3 generates this into a makefile (either that or the friendly people at torrentocracy changed it).
```

INCPATH  = -I/usr/lib/qt-3.3/mkspecs/default -I. -I/usr/local/include -I$(QTDIR)/include

```

supposedly the problem is with the QTDIR variable, but setting that didn't seem to help me run dpkg-buildpackage, and it certainly doesn't apply when I try to have pbuilder make a binary package for me.

Anybody have any input?

---

### Post by JudasReanimated on 2007-08-04
Yes please shed some light on this matter. I've truly searched through google, and found nothing besides what was mentioned above. Help would be greatly appreciated.

---

