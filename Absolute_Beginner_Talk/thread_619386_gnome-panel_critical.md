---
title: "gnome-panel critical"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Ecthelion on 2007-11-21
Hi,

I recently started having problems with my applets.

When loading them, after logging in, they sometimes just don't load correctly (can't click on them) etc.
Also, when pressing Alt-F2 the window that pops up is all messed up (entering commands still goes, but you don't see yourself typing and the window is all whited out)

I retraced the problem to gnome-panel, because when killing it and restarting a few times sometimes gets (most of) my applets straight.

This is the error that I get when, after killing it, restarting:
```
ecthelion@ElvenLounge:~$ killall gnome-panel
ecthelion@ElvenLounge:~$ gnome-panel

** (gnome-panel:8045): CRITICAL **: panel_applet_frame_change_background: assertion `PANEL_IS_WIDGET (GTK_WIDGET (frame)->parent)' failed



```

This error is really anyoning because often I can't click on "Applications", "System" etc, nor use the opened application list to switch between active programs...

Anyone who knows how to solve this?

---

### Post by Inxsible on 2007-11-21
When you kill gnome-panel, it is automatically re-started because that's how the default ubuntu has it. gnome-panel 's state is 'Restart'. you can look this up in System>>Preferences>>Sessions. The current processes tab.

so you do not need to start another instance of the gnome-panel.

---

### Post by Ecthelion on 2007-11-21
Sometimes that's true, but somehow it didn't always restarted.

Nevermind that anyway, when installing something else I noticed that synaptic started to configure a bunch of things that weren't part of what I installed.

So I guess somewhere an update went wrong and I didn't notice...

Anyway, after restarting X, everything works fine again :-)

So this problem is solved :-)

---

