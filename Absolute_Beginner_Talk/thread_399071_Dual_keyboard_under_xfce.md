---
title: "Dual keyboard under xfce"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by ac7ss on 2007-04-01
I am still trying to figure out how to make a dual keyboard layout work under xfce. 

The machine needs to be qwerty (try typing that under dvorak.) for the other users. but I require dvorak for my typing. I can load the xfce-4_xkb applet, but it won't spot the separate layout within the xorg.conf file. I can manually change it with the 'setxkbmap dvorak' command but would prefer to automate it.

Please help me with this simple problem!

---

### Post by hotani on 2007-06-20
same here (awkwardly typing this with qwerty). I have yet to figure out how to use dvorak in xfce.

---

### Post by ac7ss on 2007-12-02
> **hotani said:**
> same here (awkwardly typing this with qwerty). I have yet to figure out how to use dvorak in xfce.

The solution that I am using is to add a setxkbmap command in my .bashrc plus having a terminal run with my login. Works well enough. Likely you could add the command in a startup file for xfce and save a step.

---

### Post by ac7ss on 2007-12-03
The command I used was 
```
setxkbmap dvorak
```

---

### Post by gn2 on 2007-12-03
Applications>Settings>Keyboard Settings>Layouts and untick the "use X configuration" box.

You will now be able to add other types from the list and switch between them.

---

### Post by koleoptero on 2007-12-03
> **gn2 said:**
> Applications>Settings>Keyboard Settings>Layouts and untick the "use X configuration" box.

You will now be able to add other types from the list and switch between them.

If you could tell me how can someone configure a shortcut (like the alt+shift one) for switching layouts you would solve a great mystery for me...

---

### Post by kyleolivo on 2008-01-13
Perhaps you have already found a solution to the keyboard shortcut issue, but for the sake of completeness:

Create a bash script with the following:

#!/bin/bash
setxkbmap -option grp:switch,grp:alts_toggle us,pk

Then autostart the script on xfce load (see the link below for full instructions) and you should be able to switch layouts by pressing both alt keys.

[http://ubuntu.sabza.org/2006/10/13/xubuntu-easily-switch-keyboard-layout/](http://ubuntu.sabza.org/2006/10/13/xubuntu-easily-switch-keyboard-layout/)

---

