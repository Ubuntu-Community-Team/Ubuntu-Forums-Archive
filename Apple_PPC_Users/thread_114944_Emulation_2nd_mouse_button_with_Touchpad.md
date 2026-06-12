---
title: "Emulation 2nd mouse button with Touchpad"
date: 2006-01-09
forum: Apple PPC Users
---

### Post by el3ktro on 2006-01-09
In MacOS, when I press Ctrl and the (single) Touchpad button, I can make a "right button" mouse click. This does not work in Kubuntu, but is there a way to do so? I often don't have my mouse with me, but I often need to right-click something. The perfect thing would be if it works just like in MacOS, but any other solution would also be fine.

Tom

---

### Post by linear on 2006-01-10
Normally the right mouse button is F12. Should be the same, as you don't actually click to use it (just hover the mouse at the desired place and hit F12).

---

### Post by nkbj on 2006-01-11
You could use the 'mouseemu' package (in the Universe repository). You can set it up to use e.g. Ctrl-click as right click etc.

This is the content of my /etc/default/mouseemu file:

MID_CLICK="-middle 125 272"         # Command key + mouse click
RIGHT_CLICK="-right 29 272"        # Control key + mouse click
SCROLL="-scroll 56"              # Alt key + mouse movement
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

Regards,
Niels Kristian

---

### Post by Ptero-4 on 2006-01-12
[QUOTE=nkbj]You could use the 'mouseemu' package (in the Universe repository). You can set it up to use e.g. Ctrl-click as right click etc.

This is the content of my /etc/default/mouseemu file:

MID_CLICK="-middle 125 272"         # Command key + mouse click
RIGHT_CLICK="-right 29 272"        # Control key + mouse click
SCROLL="-scroll 56"              # Alt key + mouse movement
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

Regards,
Niels Kristian[/QUOTE]

A word of warning. It can cause odd mouse behavior.

---

### Post by nkbj on 2006-01-16
[QUOTE=Ptero-4]A word of warning. It can cause odd mouse behavior.[/QUOTE]

Yes, the mouse seems to freeze once in a while, but it is still better than no middle and right mouse buttons (I use an old Apple ISO keyboard with no function keys, so I cannot use F11 and F12).

Regards,
Niels Kristian

---

