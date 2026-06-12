---
title: "Is it just me or is it old in here?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-08-11
I've noticed in the last while here that when I apply some themes, actually like 75%, instead of actually using the theme, the "controls" all go to a very basic look, as if there is some trouble loading the parts of the theme.  What's up?!

I've attached a picture of what I mean, and what it *should* be like:

---

### Post by Teh Dust on 2007-08-11
When I was just starting to learn Ubuntu I had a problem like this. I think I was able to solve it by downloading a couple of GTK-2.0 engines in Synaptic, I also had to move the themes from /usr/share/themes to .themes hidden in the home folder.

Not sure if it will do the same for you, but worth a shot.

---

### Post by ryanVickers on 2007-08-11
Ok.  Any names you remember - I just searched "gtk" and the list was long and mostly irrelevant. :)

---

### Post by Teh Dust on 2007-08-11
The package is gtk2-engines

Edit: I tried installing the theme from gnomelooks and am having problems with it aswell. Ill see if I can get it running corectly.

Edit 2: Looks like both of us need to read details before we install a theme. it requires gtk2-engines-murrine and a modified version of clearlooks that supports GUMMY style.

Both are available when you add theese repos.
deb [http://download.tuxfamily.org/pollyrepo](http://download.tuxfamily.org/pollyrepo) feisty/
deb-src [http://download.tuxfamily.org/pollyrepo](http://download.tuxfamily.org/pollyrepo) feisty/

Personaly I find the blubuntu theme to be nice with most emerald themes and it is available in Synaptic, just search blubuntu.

---

### Post by ryanVickers on 2007-09-04
ok, thanks!  tons of themes work better now, I just installed like 50 engines and didn't even read what they do :), but you were right, that one I previewed earlier still won't work!

Just one thing - It might just be a coincidence, but the transparency in my panel (gnome) doesn't work anymore - I'm using an image with transparency, and it used to work, and now it doesn't! :(

---

### Post by ryanVickers on 2007-09-04
never mind, it's working again :)

---

