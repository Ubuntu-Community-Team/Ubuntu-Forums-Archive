---
title: "ezoom is not zooming"
date: 2008-05-24
forum: Assistive Technology &amp; Accessibility
---

### Post by joann on 2008-05-24
Hello,

I recently upgraded my system from Feisty Fawn to Hardy Heron. Before I upgrade I used ezoom on a regular basis for screen magnification. Unfortunately after the update ezoom is not working right. I cannot zoom in (or out for that matter). When I attempt to zoom in using the shortcut keys, my mouse disappears and there is no change in the zoom level. I am not sure why it is not zooming in. 

Also, when I attempt to zoom in manually using the dbus it does not zoom in either.

dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/ezoom/allscreens/zoom_in org.freedesktop.compiz.activate string:"root" int32:0x72
method return sender=:1.24 -> dest=:1.13127 reply_serial=2

Any suggestions on how to get this working properly would be greatly appreciated.

-Joann

---

