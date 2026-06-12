---
title: "AARGH! Last compiz update broke settings-manager!"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by switchcode on 2007-12-20
Yesterday I downloaded the kernel update and forgot to restart my laptop; Later in the day I downloaded another update for compiz, and compiz settings manager. Now, although I can set desktop effects to extra, the windows do not wobble, my screen-corner commands do not work (show desktop, blahblah) ANDDddd.. Compiz settings manager simply does not start. I have tried to access it through the appearance window (the preferences button within the desktop effects tab) and through the main preferences menu (Compiz config settings manager)..
  In a rush to try to correct this I have completely removed and reinstalled compiz, settings manager, and all libraries it depends on, to no avail. Here is a print of the result i get from running compiz --replace in a terminal:
```
$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Window manager warning: Failed to load theme "": Failed to find a valid file for theme 

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Everything was working perfectly before these last updates =( Failing a proper fix, could I just rollback to before the compiz update and make everything work again? =(

---

### Post by willie_wang on 2007-12-20
Try:

System >> Preferences >> Advanced Desktop Effects Settings >> Preferences (just above the close button) >> Backend >> Flat-file Configuration Backend.

Worked for me :)

---

### Post by switchcode on 2007-12-20
Thanks for the fast reply, but the preferences button doesnt work any more; its there, but it doesnt start up compiz settings manager. Also, I just noticed that emerald is no longer installed, and it is uninstallable. Synaptic says that emerald depends on a library that is uninstallable.
  Id love to solve this without reinstalling; This system was SO close to being complete =(

---

### Post by willie_wang on 2007-12-20
sorry! haven't got a clue then. this is the solution that worked for me when my compiz mussed up, but then again, i don't have emerald installed. :-\

---

### Post by switchcode on 2007-12-20
ah sokay dude; Thank you for trying; Im gonna wait another hour then bite the bullet and reinstall =(

---

