---
title: "i hate to ask but ... can someone explain what GTK is and what it does?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-09-27
wow. i know this is probably pretty high on the beginner question... but i've been looking at some GTK themes, and now i'm wondering exactly what does GTK do? i know that ubuntu (i'm running 7.04) uses the gnome "desktop". is GTK the default handler of themes for gnome? 

i like the flexibility that GTK apparently offers, but i don't know what the heck it is. is it similar to Compiz, in that you install it to add effects?

---

### Post by overdrank on 2007-09-27
> **ijason said:**
> wow. i know this is probably pretty high on the beginner question... but i've been looking at some GTK themes, and now i'm wondering exactly what does GTK do? i know that ubuntu (i'm running 7.04) uses the gnome "desktop". is GTK the default handler of themes for gnome? 

i like the flexibility that GTK apparently offers, but i don't know what the heck it is. is it similar to Compiz, in that you install it to add effects?

Hi maybe this link will help
[http://dmartin.org/make-your-ubuntu-desktop-look-slick-some-new-gtk-engines-murrine-and-candido](http://dmartin.org/make-your-ubuntu-desktop-look-slick-some-new-gtk-engines-murrine-and-candido)

---

### Post by jordanmthomas on 2007-09-27
GTK is the Gimp Toolkit, which was designed originally for, you guessed it, the Gimp.
What does it do though?  Well, It is responsible for rendering your buttons (like OK, Cancel, etc) scrollbars, everything that is themed when you change your controls theme in gnome.

Still with me?  Good, because that's about all there is to it. GTK listens for when events happen (like moving a scrollbar, clicking a button, hovering over something, etc.) and then tells the program, which does something appropriate.

That's really all there is to it.  To see an example of something that renders controls other than GTK, look up Qt programs (any kde program) and you will probably be able to see a difference, and there is a big difference when coding with them.

---

### Post by ijason on 2007-09-27
so do i need to install GTK? or is it the default handler of those graphics for gnome?

---

### Post by jfinkels on 2007-09-27
> **ijason said:**
> so do i need to install GTK? or is it the default handler of those graphics for gnome?

If you have installed the default Ubuntu desktop version, you have already installed GNOME, which is a desktop environment (a collection of programs and a window manager that look good together), and since it depends on GTK (a toolkit that provides widgets and functions for creating GUI applications), you already have it installed! Some applications designed for KDE require Qt (a different toolkit), so you may need to install those packages if you try to install a program designed for KDE.

---

### Post by jordanmthomas on 2007-09-27
GTK is already installed, unless you're wanting to write programs for gtk (which I'm guessing you're not) in which case you'd need to install the gtk headers.  Any Gnome program you have that has any sort of GUI to it uses GTK (except firefox, which kind of uses its own thing).

You may need to install engines and themes if you wish for gtk though.
The link overdrank gave you tells you how to install a new engine (which involves getting the gtk headers like I mentioned above).  Getting themes is as easy as drag-and-dropping them on the theme manager.

---

### Post by ijason on 2007-09-27
**@ jfinkels jordan** : ahhh. ok. so when i'm looking at the _>system>pref>theme_ that IS for gtk themes? and i would only need to update the engine if i want a particular theme that doesn't use the default engine to handle the graphics?

---

### Post by jordanmthomas on 2007-09-27
Yep, that's for GTK themes.  You'd only need to install an engine if you apply your new theme and it doesn't look as advertised.  Then, usually, you can find the engine in Synaptic (called gtk-engine-something) and install it and reapply your theme.  One example is the murrine engine (something you'll likely come across when looking for themes and it should be in the package manager).

---

### Post by sicofante on 2007-10-25
Do these engines take system resources? I'm installing Ubuntu in an old system and I wanted to install a Murrina theme, but I'm afraid of installing the engine just in case it takes too much resources.

---

### Post by jordanmthomas on 2007-10-25
Just installing the engine won't hurt, but using it might slow your computer down some.
With murrina themes, it's usually 50/50.  Some themes are fast, and others are slow.

It won't hurt to try it though, and if murrina themes are too slow for you, just don't use them.  :)

---

