---
title: "is it possible to make the menu.."
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by windfer on 2007-05-23
appear with the left mouse button like in fluxbox? and if so how

---

### Post by kevinlyfellow on 2007-05-23
What DE are you running?  If you are running gnome, you can run gnome on top of fluxbox (default of course is metacity).  Metacity does not support what you are looking for AFAIK

---

### Post by windfer on 2007-05-23
im running Gnome i would run fluxbox except i hate the way it looks and love the way gnome looks ye i am very vain

---

### Post by kevinlyfellow on 2007-05-23
Well, fluxbox is just a window manager, so it would look like gnome, but with fluxbox "underneath".  I used to use openbox underneath gnome

Try this out
[http://ubuntuforums.org/showthread.php?t=34239](http://ubuntuforums.org/showthread.php?t=34239)

If I remember it allows for something like what you wanted.  You can try to run fluxbox under gnome, but I'm not sure exactly how.

---

### Post by urukrama on 2007-05-23
> **kevinlyfellow said:**
> If I remember it allows for something like what you wanted.  You can try to run fluxbox under gnome, but I'm not sure exactly how.

Shouldn't that just be ```
fluxbox --replace
```

I don't use fluxbox, but that is how you use openbox in gnome (openbox --replace). If you want the right click menu on the desktop, though, you have to disable nautilus managing the desktop also.

You can add things to the nautilus desktop menu, though. Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=228371](http://ubuntuforums.org/showthread.php?t=228371)

Otherwise you could use XFCE. The right click desktop menu is default there. I beleive you can also configure KDE as such.

---

### Post by kevinlyfellow on 2007-05-23
The big problem is that you'll need to compile fluxbox from source, because the one in the repos is no good (or so I've heard).  You'll need special compile options to make it work with gnome also

Edit: Nice link :-)  I'm going to try this one out myself.

---

