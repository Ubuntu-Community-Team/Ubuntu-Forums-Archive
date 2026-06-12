---
title: "Windows like bindings possible ?"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by PingunZ on 2006-11-15
I was wondering if I could bind some popular windows bindings in linux.
- Super_L + D : Show desktop
- Super_L + R : Equivalent to alt+F2 ( run.. )
- Super_L + E : Open nautilus
- Super_L : Open Slab menu
- Super_L + L : Lock screen

Any ideas ? :)
I'm running Ubuntu 6.10 ( edgy ) i386.
My resolution is 1280*1024 ( in some cases that might me nesescary )

Cheers

---

### Post by bodhi.zazen on 2006-11-15
From your gnome menu:

Select: System -> Preferences -> Keyboard

Then select the "Layouts" tab and have at it :p

Or use Fluxbox. Edit ~/.fluxbox/keys

Icewm also has very rich features with key bindings.

---

### Post by PingunZ on 2006-11-17
Changing desktop enviroments isn't really an option.
There is no way to compare icewm and flux with gnome.
I will try what you said, does this cover all my *requested* shortcuts ? Or is there a way to make them all work ?

Cheers

---

### Post by staticsage on 2006-11-21
I accomplished all of your requested shortcuts except for locking the screen and opening the Slab menu.

You can't use the Windows key as a modifier (like control or alt) and have it open the Slab menu.

In order to make Win + D, R and E to work, first go to System -> Preferences -> Keyboard (as bodhi.zazen said). Then click the Layout Options tab and then Alt/Win key behavior. Select Super is mapped to Win-keys.

Then go to System -> Preferences -> Keyboard Shortcuts and edit:

Home folder - Hit Win + E
Show the panel run application dialog - Hit Win + R
Hide all windows and focus desktop - Hit Win + D



However, I run into trouble when trying to use Win + L to lock the screen. It just simply will not work for me. I mapped it using the Keyboard Shortcuts dialogue the same way that I did for the other shortcuts, but it won't lock the screen.

Has anyone gotten it to work?

---

