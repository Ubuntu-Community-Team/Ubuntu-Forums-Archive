---
title: "Title bar customization"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by fireslack on 2007-07-30
How do I customize the title bar at the top of a window?  I don't want to do much, just move the Close, Maximize, and Minimize buttons to the left side.  I'm a Mac user and this is the only thing about Linux that really bothers me at all.  Its not that it matters which side its on, just looking for some uniformity when I go back and forth.  I don't really want to download an entire theme because this is the only change I want to make at the moment and I want to know how to do this for future reference.   Any help is appreciated.  Thanks.

---

### Post by oilchangeguy on 2007-07-30
> **fireslack said:**
> How do I customize the title bar at the top of a window?  I don't want to do much, just move the Close, Maximize, and Minimize buttons to the left side.  I'm a Mac user and this is the only thing about Linux that really bothers me at all.  Its not that it matters which side its on, just looking for some uniformity when I go back and forth.  I don't really want to download an entire theme because this is the only change I want to make at the moment and I want to know how to do this for future reference.   Any help is appreciated.  Thanks.

you're talking about firefox, right? i don't think you can. i right clicked on the bar, and saw no option to move anything.

---

### Post by fatsheep on 2007-07-30
No I think he's talking about any GTK window.  Sorry, I don't have any idea how to move the buttons to the left side.  That's more then a theme would do...

---

### Post by RedSquirrel on 2007-07-30
I'm not sure if you can do that in Metacity (the window manager GNOME uses on Ubuntu) and I've never tried.

You can do it easily with Fluxbox. I use Fluxbox (without GNOME) and I removed the Maximize/Minimize buttons because I never use them; moving them to the left side is simple as well.

---

### Post by mcduck on 2007-07-31
Yes, Gnome's default window manager Metacity supports that. You just need to change the setting with gconf-editor:

1. Press Alt-F2 and run 'gconf-editor' to open the Configuration Editor.

2. Browse to apps/metacity/general

3. change the value of "button_layout" from "menu:minimize,maximize,close" to "close,maximize,minimize:menu" (or whatever is the order you want)..

---

### Post by fireslack on 2007-08-01
> **mcduck said:**
> Yes, Gnome's default window manager Metacity supports that. You just need to change the setting with gconf-editor:

1. Press Alt-F2 and run 'gconf-editor' to open the Configuration Editor.

2. Browse to apps/metacity/general

3. change the value of "button_layout" from "menu:minimize,maximize,close" to "close,maximize,minimize:menu" (or whatever is the order you want)..

That did the trick, thanks for the help.  I changed the "button_layout" value to "close,maximize,minimize:menu" and it  now mimics the OSX style I am used to.  Thanks again.

---

### Post by ipguru99 on 2007-09-06
Thanks mcduck!!

I had just done a dist-upgrade on my wife's laptop (from 6.06 to 7.04).  For some reason, and I have now done a bunch of these, the minimize, maximize and close were about 1/3 indented from the right... maybe 1/4.. 

But anyway, this setting was NOT in the registry (gconf.. what ever).  I put it in there and she had about three windows open... they ALL changed right there.

Sweet!

Thanks!

---

### Post by asmoore82 on 2007-09-06
> **mcduck said:**
> Yes, Gnome's default window manager Metacity supports that. You just need to change the setting with gconf-editor:

1. Press Alt-F2 and run 'gconf-editor' to open the Configuration Editor.

2. Browse to apps/metacity/general

3. change the value of "button_layout" from "menu:minimize,maximize,close" to "close,maximize,minimize:menu" (or whatever is the order you want)..

SWEET!!!

I did not know that one!

---

