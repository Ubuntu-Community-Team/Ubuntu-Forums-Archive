---
title: "i've done something stupid."
date: 2005-01-14
forum: Apple PPC Users
---

### Post by utkucan on 2005-01-14
hello,

i just installed ubuntu on my ibook as a dual boot system. i was trying to work out how to access contextual menus but neither command-click, ctrl-click or alt-click would work so i went into the mouse preferences menu and made it left handed to see a couple of the contextual menus. i then pressed enter by mistake and the mouse control remained left handed so whenever i click on my trackpad button, it right clicks. and seeing as i cannot find the alternate click shortcut, or have an external mouse, i cannot seem to fix it. does anybody have an idea on what to do?

also, moving from mac os x to ubuntu, i found the mouse being too erratic and at slower speeds just too slow. doesn anyone know of optimal setting or a piece of software that makes it similar to the mac os x mouse experience?

thank you all very much for your help in advance,

utku

---

### Post by mac-usr on 2007-05-21
An easy way to fix this is use the alt-f1 comand to open the main menu  then just use the arrow keys to scroll through and select the mouse pref and change it back.

---

### Post by Alterax on 2007-05-22
I've done the same thing myself, and it took me a bit to figure out where the alternate-click (AKA right-click was).  To save you the trouble, on my iBook G4, it's the F12 key.  If you have reversed the mouse buttons, then you can change it back the same way by using the F12 key as your mouse click.  Swap the mouse 'buttons' again from a left-handed mouse to a right one in the menu and you'll be fine.

I'm trying to decide how to remap this to a different key, maybe to the apple key since it doesn't appear to do much of anything.  Does anyone know the best way I can do this?

Alterax

---

### Post by ruy_lopez on 2007-05-22
The configuration for the mapping of mouse buttons to keys is located in /etc/sysctl.conf.

These lines in sysctl.conf
```

dev/mac_hid/mouse_button2_keycode = 87
dev/mac_hid/mouse_button3_keycode = 88
```

You use this to find the keycode:

```
sudo showkey
```

Then press the key you want.

I had problems with this command a while ago, it went into an infinite loop. I don't know what its like these days.

---

### Post by Alterax on 2007-05-23
I'll give it a try and see what it comes up with.  Thank you!

--Alterax

---

### Post by Alterax on 2007-05-23
showkey worked a bit better this way:

sudo showkey --keymap -t 3

Looped for about 30 seconds then it had the sense to stop.

The apple key comes up with character codes 96 and 91 simultaneously; I am assuming that either one of them should work if mapping it to the apple key.

--Alterax

---

### Post by pxwpxw on 2007-05-23
**Alterax**

You get diffferent result dpending on -s -k -m, see man showkey
My apple keys return nothing for showkey -m
I think you need showkey -k (or just showkey) for the keycode.

Results below for powermac, apple keyboard, left and right apple keys
I can only run showkey on a console, not on a desktop terminal.

root@bigmac:/home/admax# showkey -s
kb mode was UNICODE

press any key (program terminates after 10s of last keypress)...
0x9c
0xe0 0x5b 0xe0 0xdb
0xe0 0x5c 0xe0 0xdc

root@bigmac:/home/admax# showkey -k
kb mode was UNICODE

press any key (program terminates after 10s of last keypress)...
0x9c
0x7d 0xfd
0x7e 0xfe

root@bigmac:/home/admax# showkey -m
kb mode was UNICODE

press any key (program terminates after 10s of last keypress)...
root@bigmac:
(nothing)

---

