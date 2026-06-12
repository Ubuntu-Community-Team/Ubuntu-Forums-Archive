---
title: "theme &amp; icon question"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by zekopeko on 2006-10-11
hi,

i'm using neutronium theme from gnome-look and have a little problem with renaming files.
i can't see my cursor ( | ) when i'm renaming the file so it is a problem to see what am i doing. can i change the color of that cursor to white somehow?

the second question is that: i use diffrent icons from diffrent icon sets and every time i update some program (which has a modified icons) it gets changed back to the ubuntu default. example: firefox has a nice fancy fox but after the update it gets changed to the default globe. so how can i make my own icon set? any tutorials? btw i replace the default icons with alternate by copying over the ones in /usr/share/pixmaps 

thnx in advance

---

### Post by petersjm on 2006-10-11
There's a script somewhere to download and install the Mozilla Firefox version (as opposed to the Ubuntu-distro version) which will keep the fox-globe. See here: [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by CatKiller on 2006-10-11
> **zekopeko said:**
> so how can i make my own icon set? any tutorials?

[GNOME Icon Theme Tutorial]("http://live.gnome.org/GnomeArt/Tutorials/IconThemes")

> btw i replace the default icons with alternate by copying over the ones in /usr/share/pixmaps

If, instead of putting a different icon in /usr/share/pixmaps, you make a symbolic link from the icon you like in the theme it comes from to the equivalent place in the icon theme you're using, then you'll still get the icon after an update. So say you were using the Human theme, but you really liked the Terminal icon from the Wasp theme - then you could make a symbolic link from /usr/share/icons/Wasp/scalable/apps/gnome-terminal.svg to /usr/share/icons/Human/scalable/apps/gnome-terminal.svg.

---

### Post by crossedout on 2006-10-11
Follow petersjm advice on the firefox icon.  Follow the HowTo in my sig to have a better alternative to making your own icon theme.

-Xout

---

