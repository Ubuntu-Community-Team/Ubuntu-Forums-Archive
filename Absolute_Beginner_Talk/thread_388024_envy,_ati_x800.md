---
title: "envy, ati x800"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-03-19
well i finally installed ubuntu on the good computer too! :popcorn: :popcorn: :popcorn: :popcorn: to get it working i changed the 'ati' to 'radeon' in the xorg.conf file. i wasn't sure that was good enough for gaming & stuff so i tried envy's txt interface to configure it automaticaly. i used the txt menu thing cuz i couldn't find the program in the menus after i installed the .deb file. anyways it made my screen all green/yellow with lines so i turned off the comp, turned it back on & it looks normal again.

edit: i totally locked up & saw the green again when i tried to get to the console so i did sudo aptitude purge envy, i hope that did it.

guess i just need to know how to find out if i have the right drivers to play d2 & whatever game i move to some time later, if any.

also did i really get rid of envy? is it something i did or something wrong w/ it? next time i'll just do it the right way....bah :P

---

### Post by Kobalt on 2007-03-20
Yes that must have removed envy, but not the drivers (that seem bugy for your card) it has installed. 
I suggest you follow these instructions to set up your card properly at first : 
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html)

---

### Post by lunaz on 2007-03-20
i did do:

```
glxinfo | grep rendering
```

and it showed

```
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
gail@gail-badassness:~$
```

if i follow the rest of the directions will it make it so i can get back to 1280*1024 resolution?

---

