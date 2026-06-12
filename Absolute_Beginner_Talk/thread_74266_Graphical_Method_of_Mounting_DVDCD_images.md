---
title: "Graphical Method of Mounting DVD/CD images?"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by 51mmz0rz on 2005-10-11
I was wondering if there was an easier way to mount/unmount images (mostly iso and bin/cue), maybe via right click in GNOME.  I have installed CDEmu, and have mounted ISOs using loopback (or whatever that cmd is), but often get annoyed going back to the console again and again.  I searched these forums, but couldn't really find anything.  Being new to Linux, I was didn't know if there was such a program, or if I haven't found much because there is nothing...

---

### Post by frodon on 2005-10-11
I don't know any graphical tools which do that, however it shouldn't be dificult to create a simple Gui with **zenity** which handles cdemu for .bin/.cue and mount/umount commands for .iso file.

I just depends on how many people really needs such a GUI. If you want to develop this  GUI i have an example of a GUI i made with zenity which handle proftpd, see the attached file at the end of my [HOWTO.]("http://www.ubuntuforums.org/showthread.php?t=51611")

---

### Post by Metacarpal on 2007-01-26
Just posting in case someone searches this later - there is now a package called gisomount available in the repos.

Get it through Synaptic, or: ```
sudo aptitude install gisomount
```

It needs admin permissions to work, so run it with gksudo.

---

