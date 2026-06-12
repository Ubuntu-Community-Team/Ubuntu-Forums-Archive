---
title: "switching window managers with the CL?"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-03-12
how do i do this? i currently have fluxbox and openbox for wms. fluxbox is set up to start at *startx*. i want to be able to go back and forth between the two window managers without logging out and without using a display manager. i've tried *start openbox* and 'it' said i already had a window manager running, so then i tried *restart openbox* and was told there was no such thing as *restart* (same with *Restart*).

---

### Post by Pragmatist on 2006-03-12
Check these out in synaptic they might help:

[B]selectwm
wmanager
[/B]

---

### Post by kabus on 2006-03-12
```
xinit */path/to/wm* -- *xserver options*
```

for example, I have this alias in my .bashrc :

```
alias       rat='xinit /usr/bin/ratpoison -- -dpi 96 -nolisten tcp'
```

---

### Post by fuscia on 2006-03-12
what i want to be able to do is to switch between window managers while i'm signed in. in the right-click menu of fluxbox, there is a catagory called 'windows'. under that listing is 'openbox'. when i click on it, i find myself suddenly in openbox. the problem i have is that the same listing in openbox is in the 'Debian' menu and doesn't list fluxbox, so i can't get back to fluxbox without logging out (i have startx set up to take me to fluxbox). unfortunately, i don't know how to edit that Debian menu, as it's not an option in obmenu.

as it is a simple menu entry, i should think it would be able to dublicate in the cl. here is the way the command looks in fluxbox...

[i][submenu] (Window)
     [restart] (openbox) {openbox}[/i]

---

### Post by Pragmatist on 2006-03-12
Well I know the location and syntax for fluxbox because I have it on my system and I've used it.  The locations of the menu files are at~/.fluxbox  and  /etc/X11/fluxbox
I would first do this to find out more:
```
man -k openbox
```

Then I would use locate:
first update the database for locate to work (give this a minute to finish)
```
sudo updatedb
```

then type this:
```
locate openbox | grep menu
```

Check out the menu files, and see if they have the same syntax...etc.. and so forth :)

---

### Post by fuscia on 2006-03-12
it seems like the debian-menu will add just about any wm i install, except fluxbox. i tried adding fluxbox to that menu, using the same format as the other wms, but it kicked it out somehow.

---

### Post by Pragmatist on 2006-03-12
Where in the Debian menu is this?  What file are you adding to?  What does that file look like?

---

### Post by fuscia on 2006-03-13
[QUOTE=Pragmatist]Where in the Debian menu is this?  What file are you adding to?  What does that file look like?[/QUOTE]

right click, debian, window managers.
i can't find the file again, but it looked like xml (i wouldn't really know).

i've gotten rid of everything but fluxbox and openbox. i was using kicker and kdesktop in fluxbox and i was getting tons of errors. i just bagged it all. the important thing, for me, is that i was finally able to dump a display manager. no display manager, no file manager...life is good and sparse.

---

### Post by Pragmatist on 2006-03-13
So how do you switch between them.  Incidentally, I like a clean, simple, system myself.  I especially despise display managers.  Two questions for you:

1.) Why do you use openbox?
2.) How did you set them up to start on boot?

---

### Post by fuscia on 2006-03-14
[QUOTE=Pragmatist]So how do you switch between them. [/quote]

just click on the one you want and it switches automatically.

> Incidentally, I like a clean, simple, system myself.  I especially despise display managers.  

i've become addicted to it. and i agree: display managers are a giant waste. wdm was much more preferable than gdm and i could never get kdm or xdm to work.

> Two questions for you:

1.) Why do you use openbox?
2.) How did you set them up to start on boot?

1. well, now i'm using fluxbox and no longer have openbox on my machine. i used it because i liked the scrollable workspaces, editable menu, and it's fast. i love being able to right click on the wallpaper to get what i need. i've switched to fluxbox, which i find to be basically the same, except that it's more configurable and has better themes. it's also the first wm i have installed from source and the novelty of having done so makes it special somehow.

2. i edited both .xinitrc and .xsession by adding "exec fluxbox". when i enter "startx", it just goes into fluxbox.

---

