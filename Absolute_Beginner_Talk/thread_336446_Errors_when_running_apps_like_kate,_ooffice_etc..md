---
title: "Errors when running apps like kate, ooffice etc."
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by g0nzo on 2007-01-11
Hi!

I'm using Kubuntu 6.10, but it happend with previous version 6.06 as well. Whenever I run i.e. kate I get bunch of errors like this:

[I]X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device[/I]

These errors above are common for all apps. When starting "ooffice" I get additionaly:

[I](process:12204): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:12204): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed[/I]

I get these errors i.e. when creating new document.

Sometimes I get additional errors like:
*Xlib: connection to ":0.0" refused by server*
or
*kded: cannot connect to Xserver :0.0*

Most of the time applications work despite all these errors. However sometimes I get bunch of other strange errors (it appears to throw them randomly :) ) and the app crashes.

Any ideas how to fix that? I tried:
[I]dcopserver_shutdown
kdeini[/I]t
like somebody suggested, but it didn't help.

---

