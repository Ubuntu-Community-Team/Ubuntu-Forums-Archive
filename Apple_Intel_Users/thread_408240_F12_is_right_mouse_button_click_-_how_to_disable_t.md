---
title: "F12 is right mouse button click - how to disable that on a Mac Mini?"
date: 2007-04-13
forum: Apple Intel Users
---

### Post by janwijbrand on 2007-04-13
I recently installed Feisty on a  Mac Mini (core duo version). Things work great!

Apparently F11 and F12 are mapped to the middle and right mouse buttons respectively *by default*. This is great for users with a single button mouse, but my mouse has three buttons *and* I'd like to use F11 and F12 for application specific features. So I do not need this feature.

But now I cannot disable it anymore.

I'm even more confused since "cat /proc/sys/dev/mac_hid/mouse_button_emulation" shows me a value of "0', which I think would indicate the mouse button emulation should not even be enabled in the first place...

Explicitly passing a "0" into /proc/sys/dev/mac_hid/mouse_button_emulation, or passing bogus values in /proc/sys/dev/mac_hid/mouse_button2_keycode and /proc/sys/dev/mac_hid/mouse_button3_keycode does not have any effect.

I hope anyone has some idea what is going on here..

---

### Post by golem3 on 2007-04-13
So with the touchpad, you can't right click (right?) 

What about with a mouse?

---

### Post by ronocdh on 2007-04-13
> **golem3 said:**
> So with the touchpad, you can't right click (right?) 

What about with a mouse?

Guys, it shouldn't need to be said, but please read the whole post before replying. OP is clearly talking about a Mac Mini, which is a small desktop box, and so would not have a touchpad. I know that Apple computers are all similarly named in that they all have "Mac" in them, but there's always more information than that which can be used for identification.

The Mac models are:
[LIST]
[*]**Mac Pro:** professional-grade desktop tower
[*]**Mac Mini**: micro desktop box
[*]**MacBook**: consumer-grade laptop, integrated graphics chipset
[*]**MacBook Pro**: high-end laptops
[*]**iMac**: consumer-grade all-in-one desktop
[/LIST]

That said, I'm unable to get Feisty beta running on my MacBook Pro, so I cannot advise. =)

---

### Post by janwijbrand on 2007-11-13
It took me a loooooong while, but I finally found /etc/init.d/mousemu (at least on Gutsy). If you disable this from being started at boottime, youre F11 and F12 are, again, just normal F11 and F12 keys.

---

### Post by cyberdork33 on 2007-11-13
If you do not want mouseemu at all just do:
```
sudo /etc/init.d/mouseemu stop 
```

You can also take a look at the config file:
/etc/default/mouseemu

---

