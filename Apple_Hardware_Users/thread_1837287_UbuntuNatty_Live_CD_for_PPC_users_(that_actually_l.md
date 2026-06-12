---
title: "Ubuntu/Natty Live CD for PPC users (that actually loads)"
date: 2011-09-01
forum: Apple Hardware Users
---

### Post by OriOs on 2011-09-01
I made a [_Live-CD_]("http://alibabatimes.com/iso/or.iso") of ubuntu for the PPC Architecture. 

It's for the command-line warriors. No flashy, no fancy. 

[LIST]
[*]For wireless settings:
[/LIST]```
sudo wicd-curses
```



[LIST]
[*]For über minimalist web browsing:
[/LIST]```
links2
``` 



[LIST]
[*]Still, there's Xorg with the flwm (fast light window manager)
[/LIST]```
startx
```

You can then launch links2 in graphical mode (via the menu or the command 'links2 -g').


[LIST]
[*]To configure the keymap of the keyboard
[/LIST]```
sudo dpkg-reconfigure keyboard-configuration
```


I've made it for a powerbook with a broken hard drive, so there's no installer and the kernel is 32bits only, but I think it may help other people than me.

[_200 MB image_]("http://alibabatimes.com/iso/or.iso")

Burn it with your favorite toaster. :popcorn:

If you have any question/suggestion...

B"

---

