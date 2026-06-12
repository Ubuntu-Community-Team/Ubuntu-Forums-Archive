---
title: "monitor troubles"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Jeezus on 2008-01-25
Is there a way to make Ubuntu not default to an external monitor plugged into my laptop?

---

### Post by smurphy_it on 2008-01-25
It probably remembered the setting.  Try hitting the Fn key combination for swapping your video signal.

On my laptop for example it is Fn + F4.

---

### Post by Jeezus on 2008-01-25
on mine it's Fn+F5 but all it does is set the output to both screens at the same time, which messes with the resolution, and makes the display on the laptop kinda funky.

You don't happen to know what the scancodes for Fn+F5 and Fn+F4 are do you?

I've written some scripts to swap between my laptop monitor, and my TV, and I'm trying to figure out how to assign them to Fn+F4 and Fn+F5

---

### Post by smurphy_it on 2008-02-04
> You don't happen to know what the scancodes for Fn+F5 and Fn+F4 are do you?

Sorry, don't know those codes off hand.  Did you hit the Fn + F5 combination more than once ?

1st combination click = External Monitor only
2nd combination click = Both Monitor
3rd combination click = Laptop screen only

etc

I guess this would be too easy, but I don't suppose the scancodes are listed in the hive.  That's the best I could think to call it, as it resembles Windows registry.

Hit Alt-F2 and type in gconf-edit then check out the apps/metacity/global key bindings key, and the key below it (can't remember what that is called).

One of the keys list the program to run, the other hive lists the keys which were pressed.

In Windoze at the moment, so I can't look it up.

---

