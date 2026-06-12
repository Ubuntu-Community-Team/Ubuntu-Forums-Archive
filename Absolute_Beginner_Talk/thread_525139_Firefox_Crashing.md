---
title: "Firefox Crashing"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by ChompTheMan on 2007-08-14
Hi there.  Firefox has been crashing on me all night.  At first, I could not download a file or access the Privacy tab in Firefox preferences without crashing.  I had session manager on Tabmixplus set to automatically restore last session upon startup which would cause firefox to crash again if my previous session involved downloading a file.  I changed the session manager options to not automatically restore, deleted downloads.rdf, and cleared my private data.  This appeared to fix the issue for a few hours.  Just now it crashed again for no apparent reason other than surfing sites.  At this point I am getting a little tired of it.  I get this output in the terminal when I start Firefox:

```
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
*** Registering FoxyTunesJSModule components (all right -- a JavaScript module!)
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
```

And this output when it crashes:

```
(Gecko:6686): Gtk-CRITICAL **: gtk_widget_get_parent_window: assertion `GTK_IS_WIDGET (widget)' failed

(Gecko:6686): Gdk-CRITICAL **: gdk_window_is_viewable: assertion `window != NULL' failed

(Gecko:6686): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed
Segmentation fault (core dumped)
```

Firefox seems to work well in safe mode at the moment.  I am using Kubuntu Feisty.

---

### Post by Gnub_Daemon on 2007-08-14
I get that same error message just about any time I try to open an application from the terminal minus the second half about foxytunes.  I'm not too sure it's anything to really worry about.  However, Firefox does tend to crash on me sometimes.  Usually on YouTube.  I'm using beryl, and after an indeterminate ammount of videos, the whole window refuses to respond and turns grey, then eventually black.  I don't think that this is anything in relation to beryl itself, because it crashes in KWin too, just not the grayed out window.  Usually for me, all that is needed is to close firefox and restore the session.  Sorry I could not be of more help.  Good luck.

---

### Post by RockTonic3 on 2007-08-14
I have the same issue with trying to play video plugins...  the screen goes gray and firefox crashes.  any pointers?

---

### Post by nvrpunk on 2007-08-14
Try removing the following directory:

sudo rm -r /home/username/.firefox

sudo rm -r /home/username/.mozilla

cant remember which and I am at work on a doze box.  

Reopen firefox and hopefully that helps.  If not try reinstalling after uninstalling firefox.

---

### Post by Seisen on 2007-08-14
Disable all of your extensions then enable them  one at a time and see which one might be causing the problems. Exentions have know to cause problems with firefox.

---

### Post by RockTonic3 on 2007-08-15
no luck there.  i removed the directory and after that didn't work i reinstalled it.  

seisen, don't have any extensions installed at the moment so i don't think that's the problem

by the way, when i disable beryl, it doesn't go gray it just freezes up.  

any other ideas please?!

---

### Post by alienexplorers on 2007-08-15
Try checking out this page.
> [http://kb.mozillazine.org/Firefox_crashes](http://kb.mozillazine.org/Firefox_crashes)

---

