---
title: "OAFIID:GNOME_KeyboardApplet crash"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Peti29 on 2007-01-13
I wanted to add another keyboard layout using the Keyboard Indicator tool on the panel. When I tried to rearrange the order of the layouts by pressing "up" it crashed. Now its crashing everytime it tries to load making me unable to change keyboard layouts (it provided me a shortcut for this).
Could someone please tell me where to find a config file that stores my layouts (for this program)? I hope that by editing that file the tool will be able to run again.

Btw. What does that "dead key" mean? (The whole issue rose from that. There is a metakey named "Super" in Beryl and I suppose that was to mean the Windows key. However pressing that key has no effect. I thought that was because I have a keyboard layout with "dead keys" and so I wanted to add another with "eliminate dead keys")

Edit: found it!
/usr/bin/gnome-keyboard-properties
This is the exact same program that Keyboard Indicator is using.
And just as I hoped by deleting the last layout, Keyboard Indicator is running again :)
Still curious about the "dead keys" though...

---

