---
title: "configuring startx for console boot???"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by richieboy on 2007-07-15
i boot to the console and want to bypass gdm and kdm.  right now when i type "startx" it starts gnome.  i want to be able to start gnome, kde, or fluxbox right from the prompt without having to use gdm or kdm to choose.  i know i have to create an .xinitrc file but don't know what to put in there.

thanks,
rich

---

### Post by felicity on 2007-07-15
[This link]("https://help.ubuntu.com/community/CustomXSession") may be of help.

---

### Post by richieboy on 2007-07-15
felicity, thanks.  that's sort of what i'm looking for but maybe the .xinitrc file limits me to one "exec" choice.  typing "exec startkde" or "exec fluxbox" don't work from the console and that's what i want.  sorry if i just sounded like veruca salt.

---

### Post by felicity on 2007-07-15
I'm not sure if it's possible to do what your wanting to do, at least I don't know how personally. Perhaps try 'start gnome-session'? Or just 'gnome-session'? But I think you'll need x started first for that. I suppose you could start plain x then start a session from within it, though that's two steps instead of one.

---

### Post by felicity on 2007-07-15
Actually it might be possible to specify a location for an individual .xinitrc file. So for instance you could have a different .xinitrc file for each session you want, gnome, kde, etc., and make an alias in terminal to easily start whichever you want. But I'm not sure how one specifies a .xinitrc file. Perhaps startx /location/of/.xinit.rc ? Just an idea, not sure if it's possible.

---

### Post by richieboy on 2007-07-15
nice idea!  three .xinitrc files and maybe no aliases needed if starts takes arguments.  i'm going to try it now.
thanks,
veruca salt

---

### Post by richieboy on 2007-07-15
YOU ARE A GENIUS!  i made folders for kde and fluxbox and inserted a .xinitrc into each.  startx takes the pathname argument and it works.  thanks a lot.  if you like dostoyevsky maybe you'll like emily dickinson (they're actually very close philosophically).  in a letter to her cousin louise, emily wrote:  "i keep an ottoman in my heart exclusively for you."  mmmm.  i think that sums it up nicely.
rich

---

