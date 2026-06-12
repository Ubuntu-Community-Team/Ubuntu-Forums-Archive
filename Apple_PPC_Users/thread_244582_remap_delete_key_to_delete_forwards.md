---
title: "remap delete key to delete forwards"
date: 2006-08-26
forum: Apple PPC Users
---

### Post by goneskiing on 2006-08-26
Is there a way to remap a key so it deletes forwards (without requiring 2 keys to be pressed) ?  Likewise for home and end ?  Having just switched to a MacBook Pro from a PC, the lack of these keys is driving me nuts.  thks.

---

### Post by APU on 2006-08-27
Try "fn" + "Delete". This works out of the box on my Powerbook just like unter MacOS X

---

### Post by goneskiing on 2006-08-27
thks for info but I'm really looking for a 1 key approach.

---

### Post by rdemanow on 2006-08-27
That would require you to edit the default keymap file, or swap the key definitions in X.

Try something like 'xmodmap -e "keysym BackSpace = Delete"'

man xmodmap for more details.

showkey and setkeycodes are console utilities that can be used to modify the system keymaps.

---

### Post by Synchro on 2006-10-14
showkey looks like it should be useful, but it doesn't seem happy over an ssh session in iTerm in xterm-color mode:
```
kb mode was XLATE

(Warning: Currently running in a pseudoterminal.)
The reported keycodes are probably wrong.

press any key (program terminates after 10s of last keypress)...
```
Also, it doesn't actually do anything - pressing keys does not report keycodes, it just shows what you typed - pressing delete or backspace produces no output at all. getkeycodes is similarly unhelpful:
```
Plain scancodes xx (hex) versus keycodes (dec)
0 is an error; for 1-88 (0x01-0x58) scancode equals keycode

KDGETKEYCODE: No such device
failed to get keycode for scancode 0x5a
```

The problem I'm trying to fix is that the normal backspace key on my MacBook (also on a G4 with an Apple pro keyboard) deletes to the right instead of left - on a full keyboard both backspace and delete keys delete to the right, with the added bonus that pressing delete at an empty prompt will kill the SSH session (but works ok the rest of the time)! It's definitely a problem at the ubuntu end as the keys work correctly with the same settings when talking to various other OSs.
I'm only interested in console fixes as I don't have a desktop or X installed on my servers.
dumpkeys produces interesting looking output, but I don't know how to make use of it.

---

