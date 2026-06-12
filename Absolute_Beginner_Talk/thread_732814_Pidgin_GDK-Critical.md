---
title: "Pidgin GDK-Critical"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by tomor on 2008-03-23
I recently upgraded from version 2.2.1 of Pidgin to 2.4.0 by uninstalling the old version and compiling the newer version from source. When I try to run pidgin from Run by writing pidgin no window appears and when I write pidgin in terminal I receive this error: 

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(pidgin:18372): Gdk-CRITICAL **: gdk_display_get_name: assertion `GDK_IS_DISPLAY (display)' failed
Pidgin 2.4.0


What could the problem be ?

---

### Post by Oldsoldier2003 on 2008-03-23
> **tomor said:**
> I recently upgraded from version 2.2.1 of Pidgin to 2.4.0 by uninstalling the old version and compiling the newer version from source. When I try to run pidgin from Run by writing pidgin no window appears and when I write pidgin in terminal I receive this error: 

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(pidgin:18372): Gdk-CRITICAL **: gdk_display_get_name: assertion `GDK_IS_DISPLAY (display)' failed
Pidgin 2.4.0


What could the problem be ?

did you get do apt-get update and apt get upgrade and get  pidgins build dependencies before trying to compile? if all else fails getdeb.net has pidgin 2.4.0 available for download

---

### Post by tomor on 2008-03-23
THANK YOU. 

I downloaded it from getdeb and it works. 

Thank you very much!

---

