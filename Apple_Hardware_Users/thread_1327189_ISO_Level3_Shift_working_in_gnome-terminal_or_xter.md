---
title: "ISO_Level3_Shift working in gnome-terminal or xterm , but _not in gtk applications"
date: 2009-11-15
forum: Apple Hardware Users
---

### Post by stereo on 2009-11-15
hi,

i have a strange problem since karmic. i'm using the german variant of an old imac keyboard. i'm used to map the right alt key to the right apple key.  in my .xmodmap stands a keycode 134 = ISO_Level3_Shift

in karmic, it works just in x-terminals, gnome-terminal oder xterm. but _not_ in normal gtk apps. on the same screen, different behaviour.

any ideas?

would be great...   


greets,
stereo

---

### Post by stereo on 2009-11-15
it works

i found it in:
[http://ubuntuforums.org/showthread.php?t=1297851](http://ubuntuforums.org/showthread.php?t=1297851)


a simple 

echo clear mod4 | xmodmap -

helps.

---

