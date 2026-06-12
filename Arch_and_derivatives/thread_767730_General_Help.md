---
title: "General Help"
date: 2008-04-25
forum: Arch and derivatives
---

### Post by YodaMstr on 2008-04-25
Alrighty guys, I'm pretty new to Arch, and I was wondering if anyone would mind giving me some help on a few unrelated questions.

1.  I run GNOME, and my taskbar applet doesn't flash whenever it wants to draw attention to the window.  Like upon receiving a message on Pidgin.

2.  Uninstalling a program that was compiled from source.  What's the best way to go about this?

3.  Compiz/Compiz-Fusion.  What packages are compiz before the merger, or are they all required for Compiz-Fusion?  And I'm having a bug where the title bar for different windows becomes botched when I have Compiz running.  Any ideas?


Those three answers would help me greatly, and I'd appreciate it.

---

### Post by finferflu on 2008-04-26
Well I can only reply to the 2nd point:

The best way of building a package from source is using the fantastic Arch Way, a PKGBUILD. You write one giving it the building instructions and it will create an Arch package for you. See [the wiki](http://wiki.archlinux.org/index.php/PKGBUILD) ;)

---

### Post by YodaMstr on 2008-04-27
Alright, thanks, I appreciate it.  Would you mind being on the lookout for what I'm describing in point one though?  I've moved to AWN, and there was a brief spell where the icon WOULD bounce to show that it wants your attention, but now it's stopped, so I guess it was just a fluke.  That and a compiz bug I'm having are the only two things that are REALLY breaking me at the moment.

---

### Post by finferflu on 2008-04-27
Well, I'm not really a Gnome expert, I haven't really used it extensively, however, you can try to rename your current Gnome config folders, and see if that makes a difference. Do:

```
mv ~/.gnome ~/.gnome_old
```

and

```
mv ~/.gnome2 ~/.gnome2_old
```

To be sure, rename also the gtk config file:

```
mv ~/.gtkrc-1.2-gnome2 ~/.gtkrc-1.2-gnome2_old
```

Then log out and re-log in, and see if everything works well again.

---

### Post by czarr on 2008-05-02
I think you just need to enable the blink in pidgin itself. In openbox i rightclick on the tray icon and select "blink on new msg". If you want the actual item on the panel to blink you need to enable one of the included plugins

---

