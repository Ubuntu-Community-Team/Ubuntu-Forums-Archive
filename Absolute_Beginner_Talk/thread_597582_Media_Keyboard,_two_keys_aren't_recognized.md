---
title: "Media Keyboard, two keys aren't recognized"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2007-10-30
I have a logitech media keyboard, all the extra keys work, (vol+/-, rewind, home, play/pause, etc.) except a zoom key. These keys are located right next to the shift and control keys, and I wanted to assign them to switch desktops left and right, the only problem is the Keyboard Shortcuts preferences won't recognize it. It recognizes all my other keys as 0xa0, 0xae, etc, but nothing happens when I press the zoom in/ out function.
Any help is appreciated. Thanks.

---

### Post by kebes on 2007-10-30
You can remap those keys to become keys like "F20" or "F21" ... which don't appear on a normal keyboard, but are nevertheless recognized by Linux (so you'll be able to set them as the shortcut key for whatever action you want).



To do this, first run a little program called "xev"... this program opens a small window, which will show the keycode for any key you press. Then you can press those keys and take note of what the number was.


You can then remap that keycode to be a different key by using "xmodmap".  For example, if the special key had keycode "234" you could have a script like:
```
#!/bin/bash
xmodmap -e 'keycode 234=F20'

```
So that now that special key is basically the 'F20' key. You will have to set this script to auto-run on boot or login. (Or add that line to a login script you already have.)



Once that xmodmap command is issued, however, the special key should be "F20" as far as Linux is concerned, so you can set that as the keyboard shortcut wherever you want.

Hope that helps.

---

### Post by Romanus81 on 2007-10-30
I tried xev, and it recognized when I pressed other buttons, but it wouldn't do anything when I pressed the zoom in/out button.

---

### Post by Romanus81 on 2007-10-30
I found this:
[http://www.kernel.org/pub/linux/kernel/people/jikos/random/hid-make-extra-keys-on-logitech-s510-work.patch](http://www.kernel.org/pub/linux/kernel/people/jikos/random/hid-make-extra-keys-on-logitech-s510-work.patch)
Which looks exactly like what I need, it seems to be a patch, but I don't know how to use it, can anyone make sense of what I need to do?

---

