---
title: "Map right command key to alt-gr (ISO_Level3_Shift)"
date: 2009-10-22
forum: Apple Hardware Users
---

### Post by proycon on 2009-10-22
I use a custom XKB keymap in which I access special characters using the alt-gr key, for example alt-gr + c -> ç. Now on my Macbook Pro, the alt-gr is a little bit too far to the right for my taste, and I keep pressing the right command key instead. Since I have no need for this key, I thought I'd simply remap it to alt-gr as well. 

I added the following to my XKB layout ( /usr/share/X11/symbols/ )
 include "level3(rwin_switch)"

The gnome keyboard settings tool also has an option for doing a same thing graphically. However, it does not work in GTK/Gnome applications! IThe settings works fine in X itself and other applications like QT apps. But in Gnome, both alt-gr and the right command key cease to function. I think this is a bug so I filed a bug report here: [https://bugzilla.gnome.org/show_bug.cgi?id=599270](https://bugzilla.gnome.org/show_bug.cgi?id=599270) .

I wonder if anybody else has come across this problem and possibly found a solution?

---

### Post by lillem4n on 2009-10-29
I have the exact same problem. Would be lovely with a solution to this. :)

---

### Post by tobixyz on 2009-10-30
as described in [https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/410876/comments/6](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/410876/comments/6) 
commenting out 
```
modifier_map Mod4 { <LWIN> };
modifier_map Mod4 { <RWIN> };
```
in
```
/usr/share/X11/xkb/symbols/pc
```

got my 3rd-level-chooser working again on my macbook-2,1.

---

### Post by beaufils on 2009-10-31
Same problem with Karmic on MacBookPro 3,1. Fixed it with something close to previous post:

```
echo clear mod4 | xmodmap -
```

---

### Post by proycon on 2009-11-01
Thanks! Works like a charm now!

---

