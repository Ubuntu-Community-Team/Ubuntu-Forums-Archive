---
title: "How do I customize my keyboard?"
date: 2008-02-10
forum: Apple Intel Users
---

### Post by _kresten on 2008-02-10
Does anyone in here have any experience in customizing the keyboard layout?

I want to make the layout on my dual booting 1st generation MacBook act like it does in OS X. As it is at the moment I am not even able to do an "at" (@) or hard parenthesis (and a number of other keys). Oh. And by the way: To complicate things I'm using a danish keyboard.

Therefore: Does anyone know about a "map" of the signs, the keys and perhaps a nice guide to xmodmap (isn't that what it is called?)?

Oh yeah: And feel free to post any experience with moving keys on macs.

---

### Post by kidders on 2008-02-11
Hi there,

I use a Mac keyboard on my PC ... it's one of those odd-ball "Europe Edition" US keyboard layouts, so standard keymaps don't tend to get everything quite right. Having said that, the place to start is with your keymap ... even if you *know* none of them are quite right. Try to find a generic keyboard layout that's reasonably close to what you've got ... a standard Danish PowerPC layout or something similar ought to do the trick.

Once you've done that, you can use xmodmap to fix any remaining weirdness. For example, without help, the international US power_g5 layout I picked for my keyboard gets my tilde/backtick key wrong, doesn't recognise F13-F16, puts the Euro symbol in the wrong place, ignores my volume/eject buttons, and so on. I corrected these kinds of things with xmodmap...```
keycode 116 = Mode_switch
keycode 113 = ISO_Level3_Shift
keycode 204 = XF86Eject
keycode 182 = F13
keycode  94 = grave asciitilde
keycode  49 = section plusminus
keycode  11 = 2 at currency EuroSign
etc...
etc...
```Something similar ought to work for you. You can use "xev" to grab the keycodes for keys you want to alter. As a general guide though, if you find yourself creating any more than about 15 xmodmap rules, you've probably picked the wrong initial keyboard layout.

Anyhow, I don't see any reason why you won't be able to configure your keyboard to work whatever way you'd like it to. Just remember to put your Xorg and Xmodmap configurations away somewhere safe, so only ever have to go to all the trouble once in your life!

---

