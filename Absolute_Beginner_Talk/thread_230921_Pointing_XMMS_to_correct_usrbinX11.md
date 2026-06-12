---
title: "Pointing XMMS to correct /usr/bin/X11?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-08-06
I've installed XMMS.

I want to listen to:

[http://boss.streamos.com/wmedia/csps/clerks_office/service/church_service.wvx](http://boss.streamos.com/wmedia/csps/clerks_office/service/church_service.wvx)

FireFox offered to open Movie Player (default), which wouldn't work as the file is a .WVX, I tried to point the file to:

/usr/bin/x11/XMMS, but that must not be where the executable file is.

I'm lost, and I apologize for having "not a clue" as to where to look for the correct executable-file, or whatever. I've only been using Ubuntu since January of this year.

Sorry to take your time for this and thanks.

---

### Post by fourchannel on 2006-08-06
most executables are located in /usr/bin/<program>

if you open a terminal and type ```
whereis xmms
``` then the first thing it displays is the location of xmms, which I can tell you on my system is ```
kev@Rei:~]$ whereis xmms
xmms: /usr/bin/xmms /usr/lib/xmms /usr/bin/X11/xmms /usr/share/xmms /usr/share/man/man1/xmms.1.gz
kev@Rei:~]$

```

the /usr/lib/xmms is the library /usr/bin/X11/xmms I have no idea what that is, and /usr/share/man/man1/xmmg.1.gz is the manual pages or help files for xmms.

---

### Post by Mark_in_Hollywood on 2006-08-06
Thanks, I get the same, with the whereis xmms, but which one "plays"? I have looked at all of the responses from the whereis, but only two are listed as executable. Both, upon being "invoked" or called (clicking with mouse pointer), load xmms and open xmms' file manager, but neither play a sound.

One and all:

Please hold off on any work on this. I have XMMS installed less than 4 hours and just now found how to "Play" a location. Maybe that will solve the problem.  THANKS.

---

