---
title: "[SOLVED] I've installed XGL, now my system is being weird."
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2008-01-27
I just installed XGL yesterday and then I shut down my system last night; this morning is the first time I've booted up since the install.  Now my computer is doing some odd things:

**1)** I have no sound.  Everything in the volume control and Alsamixer appear to be the same since before XGL.
**2)** Graphic rendering seems much slower.  I've using the restricted ATI drivers but since XGL, moving windows is choppy, looking at the screensaver selection (in the little window, not the preview) is *very* slow.
**3) **Even when power management turned off, after about 10 minutes my monitor goes into power-save mode and shuts off.
**4)** Every time I boot I get a message saying, "The X server keyboard settings differ from your current GNOME keyboard settings".  I've been choosing "keep GNOME settings" but each logon causes this message to appear.
**5)** After XGL was installed and I booted up, it told me that I could disable XGL for the current user by creating a ~/.config/xsever-xgl/disable file.  I did that, now graphics render faster, but I'm still running into #1, 3, 4 above.

What do I do?  :confused:

---

### Post by toastysquirrel on 2008-01-27
perhaps it boils down to: 

 How can I **uninstall** XGL from Gutsy?

---

### Post by finer recliner on 2008-01-27
XGL is meant to be run with compiz. if you have compiz disabled but XGL enabled, things will render noticeably slower, this is a known issue.

to disable XGL from starting up when you log in, drop an empty disable file in ~/.config/xserver-xgl. this does not uninstall it, only disables it.

```
touch ~/.config/xserver-xgl/disable
```

---

### Post by toastysquirrel on 2008-01-27
> **finer recliner said:**
> XGL is meant to be run with compiz. if you have compiz disabled but XGL enabled, things will render noticeably slower, this is a known issue.

to disable XGL from starting up when you log in, drop an empty disable file in ~/.config/xserver-xgl. this does not uninstall it, only disables it.

```
touch ~/.config/xserver-xgl/disable
```
Unfortunately I've already tried that, so I've got the speed back.  But I'm still getting that message about **"The X server keyboard settings differ from your current GNOME keyboard settings" **every time I log in.  Not to mention my sound has mysteriously vanished.

I figured out uninstalling XGL from Synaptic, unfortunately that hasn't fixed my sound problem or the message I just posted above.  Maybe I should post that in a new thread? <shrugs>

---

### Post by toastysquirrel on 2008-01-27
Under the keyboard configuration, I clicked the "reset to default" button and that seems to have fixed it.  So:

**1)** I disabled XGL per Fine Recliner's suggestion.
**2)** "Reset to default" the keyboard layout.
**3)** In Alsamixer, turned the PCM setting back up to max (it was down to zero).

Three for Three, not bad at all.  Strange... but not bad at all.

---

