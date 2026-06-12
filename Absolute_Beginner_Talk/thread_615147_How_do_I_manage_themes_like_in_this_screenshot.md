---
title: "How do I manage themes like in this screenshot:"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by sc2 on 2007-11-16
This is the theme I'm wanting to install...

[http://gnome-look.org/content/preview.php?preview=1&id=67918&file1=67918-1.jpg&file2=&file3=&name=MurrinaSane](http://gnome-look.org/content/preview.php?preview=1&id=67918&file1=67918-1.jpg&file2=&file3=&name=MurrinaSane)

How do I navigate to that window so I can change the settings? So that the theme looks like it does in the screenshot..

---

### Post by Paul820 on 2007-11-16
That's thewidgetfactory, you can't actually change the themes with that. It is only for testing how they will look. If you want to change a theme you need to look inside the GTKrc file in the .theme directory inside home. It's hidden.

---

### Post by sc2 on 2007-11-16
> **Paul820 said:**
> That's thewidgetfactory, you can't actually change the themes with that. It is only for testing how they will look. If you want to change a theme you need to look inside the GTKrc file in the .theme directory inside home. It's hidden.



Well, how come the windows aren't transparent for me? But they are in the screenshot?

---

### Post by StephUb on 2007-11-16
maybe he just shaded them ????

---

### Post by sc2 on 2007-11-16
> **StephUb said:**
> maybe he just shaded them ????

And I wouldn't know how to do that.. :x

---

### Post by jordanmthomas on 2007-11-16
To make windows transparent you'll need some kind of compositing manager.  compiz is probably the most well-known.

If you can't run compiz for some reason, you can use xcompmgr and transset.

---

### Post by Sims2789 on 2007-11-16
> **jordanmthomas said:**
> To make windows transparent you'll need some kind of compositing manager.  compiz is probably the most well-known.

If you can't run compiz for some reason, you can use xcompmgr and transset.

Compiz is already installed if you have Ubuntu 7.10 but it may not be activated by default. To activate it, make a file in the text editor called compiz.sh (or anything.sh) and put this in it:

<pre>#!/bin/sh
SKIP_CHECKS=yes compiz --replace</pre>

Then, on your desktop, right-click and select Create Launcher. Name it "Compiz On" or something like that and browse for compiz.sh. Then, when you double-click the icon (it looks like a springboard by default) Compiz will run.

This lets you turn Compiz on if you don't want it on at start-up (on Intel graphics cards, Compiz has issues with media files; Movie Player crashes on most files but Rhythembox handles audio correctly). If you want a launcher that turns Compiz off just make a file called compizoff.sh and put this in it:

<pre>#!/bin/sh
SKIP_CHECKS=no compiz --replace</pre>

To enable it on start-up, go to System -> Preferences -> Sessions and add a new start-up program, and browse for compiz.sh again.

Now you'll have custom graphics but you won't be able to customize them. To do this, go to Applications -> Add/Remove and search for CompizConfig. When you install it it'll appear under System -> Preferences as Advanced Desktop Effects Manager.

Now, if you want Vista-esque (and other cool) window borders, go to System -> Administration -> Synaptic Package Manager and search for Emerald. This manager is separate from the other advanced desktop effects.

---

### Post by sirlancelot on 2007-11-16
The above method is very convoluted if you have Ubuntu Gutsy and want to enable CompizFusion. Just do the following:

In the menu: System -> Preferences -> Appearance

Click on the VIsual Effects tab and set your preference.

If you'd like more control, you can install the "compizconfig-settings-manager" and then a 4th option where be available in the Visual Effects tab that allows you to customize CompizFusion.

Enjoy!

---

### Post by jordanmthomas on 2007-11-17
Also, to make a window transparent once running compiz, hold alt and use the scrollwheel on your mouse.

---

### Post by Aquaman420 on 2007-11-17
Thanks for the tip Jordan.  I never knew I could do that!!

---

### Post by Myglaren on 2007-11-17
Wonderful stuff. 
 *Wheeeeee.* new toys.
Vista eat your heart out.

---

