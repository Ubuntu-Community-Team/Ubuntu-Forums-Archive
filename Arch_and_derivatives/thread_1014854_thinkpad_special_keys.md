---
title: "thinkpad special keys"
date: 2008-12-18
forum: Arch and derivatives
---

### Post by zephyrus17 on 2008-12-18
I have a T61p. After the recent xorg upate, a lot of my dedicated keyboard keys won't work anymore. Like volume controls, media controls, etc.

I've downloaded tpb, but I'm not really sure I know how to configure it. nvram is in my modules. I've been to thinkwiki, but that just confuses me further.

Any help?

---

### Post by Mark Gyver on 2008-12-21
Try [this](http://wiki.archlinux.org/index.php/Xorg_input_hotplugging#How_can_I_get_the_correct_keyboard_layout_.28keymap.29.3F_I_have_lost_arrow.2Fspecial_keys).  I'm also using a T61p and had such an update a couple weeks ago.  Before the update the special keys weren't recognized at all, but I didn't want to bother fixing that.  After the update, I had to change my xorg.conf to get X to start and then there were really odd key behaviors, but then I found and followed those directions and it works much better than before.

---

### Post by zephyrus17 on 2008-12-21
So your keyboard is completely ok now? All keys are ok?

Is this a workaround or the proper way to manage this Xorg thing?

---

### Post by fwojciec on 2008-12-21
The proper way now is to use xorg-server/hal hotplugging rather than defining things in xorg.conf.

---

### Post by OutOfReach on 2008-12-21
On my Dell laptop I use xbindkeys for my media keys (Play, Pause, Volume Up/Down, etc). You can find the key code for the media keys in the 'xev' just type in 'xev' into a terminal, push a media key and watch for the ouput in the terminal and add it to your .xbindkeysrc.

Or you can type in 'xbindkeys -k' and then push your media button, it will give you exactly what to put into your .xbindkeysrc (except the part with "(Scheme function)", replace that with what you want to execute, for example if you want volume up, "amixer -q set Master 2+ unmute") and add it to your .xbindkeysrc.

I'm not sure if this is exactly what you are looking for, but I hope it helped in a way.

---

