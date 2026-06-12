---
title: "Gdk errors and Gimp 2.2.13"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-05-28
Please read carefully before posting any solutions as I've been repeating myself to countless of people. 

So, Gimp has been crashing across several installations of Feisty and due to various reasons, I am unable to use Gimp 2.3.###

My current version of Gimp = 2.2.13

What happens when Gimp crashes?
Basically, it will crash when I am saving a file as (Ctrl + Shift +S) or Saving a file(Ctrl+S) with or without using keyboard commands.

And sometimes, it will disappear from the taskbar and yes, I checked my other workspace to ensure it was not there. 

Finally, I checked .xsession-errors and found these messages:

> (Gecko:11596): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(Gecko:11596): Gdk-CRITICAL **: _gdk_window_destroy_hierarchy: assertion `window != NULL' failed

(Gecko:11596): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
checking for valid crashreport now
checking for valid crashreport now

(script-fu:7696): LibGimpBase-WARNING **: script-fu: wire_read(): error
checking for valid crashreport now
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
_gdk_window_destroy_hierarchy: assertion `window != NULL' failed

I believe the X errors refer to Wacom devices in xorg.conf and thus, have edited the devices out. However, any idea what the other Gdk errors relate to?

Edit: My bad. It appears that Gecko = Firefox errors.

---

### Post by Lucifiel on 2007-05-28
Okay, so I was asking around in #gimp

[04:34] <schumaml> you should check the window hints, maybe something changes them to utility window

[04:36] <schumaml> hidan: this is related to X11, check the available utilities for it

Anyone knows what are "window hints"?

Edit:

> From [http://www.cyvos.net/index.php?n=User.StatusAndUtilityWidgets](http://www.cyvos.net/index.php?n=User.StatusAndUtilityWidgets)

A utility window is one that only exists to provide a peripheral function. The presence of such windows can be filtered in process and window lists accordingly; the following example shows utility windows being shown in a separate list. They could alternatively be merged in with task windows or hidden altogether.

---

