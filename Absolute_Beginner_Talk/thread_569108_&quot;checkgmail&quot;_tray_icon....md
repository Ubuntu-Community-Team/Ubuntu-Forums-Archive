---
title: "&quot;checkgmail&quot; tray icon..."
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-10-06
Do you know what I mean?  Not the one with the big almost-square icon that's red and blue, I mean the smaller one with grey or red, and it uses the atom feeds, and it doesn't have a transparent background so you have to pick a colour that matches?  Well, yeah, that's the problem - I don't want to pick a colour - why can't it just be transparent!

I know I could use the other one (described first), but I found it slow, unstable, and I just _***really***_ **didn't** like it :)  So, I have the other one now, and just one complaint, the background - why can't it be transparent!? Does someone know how to change this?

I've attached an image of what I mean...

---

### Post by linuxwizard on 2007-10-06
Why isn't the tray icon background transparent?

First off, please note that you can set the background of the tray icon to whatever colour you want in the preferences, and you can even use an eyedropper to do it - it should be easy enough to get close to the real thing ...

But why not "real" transparency? Well, the simple answer is that transparency was never a feature of Gtk's trayicon libs. Gaim does it by using a patched version of the relevant lib - but that's not something you can do with Gtk2-perl. The good news is that it has recently been fixed and will apparently be included in the next major Gtk release - see this Gtk bug for details ... 

[http://checkgmail.sourceforge.net/](http://checkgmail.sourceforge.net/)

---

### Post by ryanVickers on 2007-10-06
Well, it just seems strange that there isn't some way to fix it because every other app does it! :)

Edit: I guess I've got it matching pretty well now, but it's still a pin, and it's not always perfect!  Some panels are EXTREMELY hard to match! :)  Say, if it's retty much fading from white to black ;)

---

