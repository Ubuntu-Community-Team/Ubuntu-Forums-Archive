---
title: "Video resolution, is it possible to...."
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by qwazert on 2006-03-04
...delete the modes that I will never use?
Even with my 19" monitor, I don't envision using a resolution of 1900 X 1200, but I think this might be what is screwing with my fonts and resolutions when I use other Desktops and WM's.

---

### Post by bscbrit on 2006-03-04
Yes, its very easy to do.  Simply delete the unwanted resolutions from /etc/X11/xorg.conf using a text editor.  You will have to use 'sudo' to do this.  Restart X, and its done. Be careful, if you corrupt the file you might find yourself temporarily stuck with a command line only. :D

---

### Post by qwazert on 2006-03-07
OK, so do I just delete the unwanted resolution, or the entire section pertaining to that resolution?

---

### Post by az on 2006-03-07
Boot into recovery mode and run

dpkg-reconfigure xserver-xorg
and untick the unwanted resolutions from the list, when asked.  Take the default for everything else.

This approach will survive xorg upgrades, while manually editing the file may not.  It's easier, too.

Run
init 2
to get back into the desktop from recovery mode.

---

