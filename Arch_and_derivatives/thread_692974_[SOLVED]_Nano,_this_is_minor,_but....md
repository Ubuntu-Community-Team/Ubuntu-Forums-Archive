---
title: "[SOLVED] Nano, this is minor, but..."
date: 2008-02-10
forum: Arch and derivatives
---

### Post by bwtranch on 2008-02-10
Hi, no real problems. I like it:) I have one annoying problem with nano that I can't figure out. The text that I need to edit or have edited is in this super light green that is almost impossible to read. I have to use gedit to see anything and I like nano better. One more thing, the fonts I download don't seem to be showing up. I seem to have the yucky ones still.

Thanks!

---

### Post by fwojciec on 2008-02-10
For fonts: make sure that the font paths defined in xorg.conf are correct; also, run mkfontdir (and mkfontscale -- though I'm not sure this one is really necessary) in all the font directories (navigate to the directory and then run it as root).

The nano problem is probably a problem with how your terminal colors are defined.  I don't know which terminal app you're using -- for urxvt/xterm the colors are defined in .Xdefaults file, if you're using gnome-terminal or xfce terminal the colors are set using their own internal configuration/preferences.

---

### Post by bwtranch on 2008-02-10
Hi, I fixed both problems by increasing the resolution to the fonts. We up to 130, kinda high, but I'm about blind and my screen is big, so it's Otay:)
Funny thing is and I don't know if it's all that kosher, but I used the nvidia-config app to generate an xorg-config file. It made a generic one and it called it /etc/X11/XF86.config . I guess that's Ok, it works fine. KISS, I guess. Have a good one:)

---

