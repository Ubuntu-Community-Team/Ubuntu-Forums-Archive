---
title: "[SOLVED] macbook/pro keyboard layout causes XKB error"
date: 2009-01-09
forum: Apple Hardware Users
---

### Post by franki.macha on 2009-01-09
since yesterday i've lost use of my [ctrl] key on my santa rosa macbook 3,1
as i'm sure you can all imagine, this is highly annoying.
anyway, here's the details:  [https://bugs.launchpad.net/ubuntu/+bug/314766](https://bugs.launchpad.net/ubuntu/+bug/314766)
or here: [http://pastebin.com/m50c9728c](http://pastebin.com/m50c9728c)

if anyone can help, i'll love you forever. opening new tabs, copy and pasting, selecting all, have become very tedious tasks :(

---

### Post by bryonak on 2009-01-09
Could you specify whether you changed *anything* that could have made it not work since yesterday?
Things like mapping it to a shortcut, using xbindkeys or similar tools.

Try changing the keyboard layout in System -> Preferences -> Keyboard -> Layout.

More troubleshooting:
Open a terminal and type ```
xev
```
If you move the mouse into that little window, it will show all "command input" to your computer in the terminal it was opened from (mouse movements/buttons, keyboard, ..). Now hit the Ctrl key and tell us what happened.

---

### Post by franki.macha on 2009-01-09
as far as i know i haven't changed anything, there have been a few updates in the last couple of days but i've looked through synaptic's history and none of them seem to be x related to me..


if i try and change the keyboard layout in any way i get the same error message pop up and it seems to make no difference, however i have discovered that ctrl+shift works, so i can paste into my terminal etc.

here's my xev output:

FocusOut event, serial 28, synthetic NO, window 0x4c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 28, synthetic NO, window 0x4c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 28, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

---

### Post by bryonak on 2009-01-09
This is what it should look like when you press and release the Ctrl key:
```

KeyPress event, serial 35, synthetic NO, window 0x4000001,
    root 0x13b, subw 0x0, time 16309747, (2,37), root:(1156,587),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x4000001,
    root 0x13b, subw 0x0, time 16310227, (2,37), root:(1156,587),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```


Your output is remapped, either by Compiz, Gnome or applesmc.
It looks like a shortcut for increasing/decreasing volume/brightness or triggering compiz effects.

The trivial problem would be that you have mapped Ctrl within CCSM or Gnome's shortcuts dialog.

---

### Post by franki.macha on 2009-01-09
doh, thank you bryonak, it was compiz :D
although, the bug/error messages persist, i have use of my ctrl key again now, and feel rather silly too :)

---

