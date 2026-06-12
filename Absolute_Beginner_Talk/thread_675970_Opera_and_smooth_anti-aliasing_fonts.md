---
title: "Opera and smooth anti-aliasing fonts"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by hspdion on 2008-01-23
Hi,

New to Ubuntu and I'm trying to get my preferred web browser to look nice when displaying pages and its just not happening.

I installed the mscorefonts from the repositorieswith the Synaptic Package Manager. Following the advice of other threads I've gone under opera:config and unchecked 'Enable Core X Fonts' and then restarted Opera. At first, this does works and makes the program's fonts silky smooth. When I restart the system, however, Opera's font rendering is back to its former ugly self. Rechecking and/or Unchecking 'Enable Core X Fonts' in Opera from this point on has no effect on its font rendering. 

I've tried this with both the 9.25 version from the repositories and the 9.50 alpha builds available from opera.

Any ideas?

---

### Post by furball_1185 on 2008-01-23
Have you tried smoothing the fonts at the display manager level? Under the System > Preferences . Appearance menu item there is a section for fonts. Enable some form of sub-pixel smoothing method (like the one suggested for LCD monitors), restart your display manager (ctrl+alt+backspace) and you should see much crisper fonts everywhere.

Hope this helps.

---

### Post by hspdion on 2008-01-23
Yes I have the fonts smoothed at the display manager level. Firefox and every other app looks great, except Opera.

---

### Post by pjalegria on 2008-04-12
Same problem, opera fonts suck...

---

### Post by dwblas on 2008-04-12
I use New Century Schoolbook in Opera and like the way it looks.  I have installed so many fonts that I'm not sure if New Century is installed by default on Ubuntu, or where it is in the repositories though.

---

### Post by MyR on 2008-04-15
you can change the fonts opera uses, both for webpages and for opera itself.

---

### Post by Pigeon. on 2008-07-17
Using the standard Gnome stuff doesn't affect Opera. Opera is a Qt application and therefore its font rendering can be controlled via KDE. Launch kcontrol and play with the font section, apply changes, then restart Opera.

---

