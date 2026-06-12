---
title: "Run console programs at startup"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by joewhite on 2006-05-30
I have made a script to run programs at start-up for XFCE. The script is being detected but the console programs like htop and alsamixer do not run. Only graphical programs open up. The XFCE session manager also fails to reload console programs. It only reloads the terminal windows that contained these programs from the last session. How do I get the console programs to stay up in a terminal at start-up? Also are there any commands to set the window position for these terminals, preferably for xfce-terminal? I am aware that gnome-terminal can use profiles to load a program at startup but I would prefer to stick with xfce-terminal. Thank you.

---

### Post by vidak on 2006-05-30
are you searching for something like
xterm -exec alsamixer
?

---

### Post by joewhite on 2006-05-30
Yea thats right. I guess I can just run them in an xterm it will be faster. Thanks.

---

### Post by vidak on 2006-05-30
the -exec option could/should work with other terminal emulators too..

---

### Post by mostwanted on 2006-05-30
Just to clarify, the programs are indeed running you just don't see them because they're not launched in a terminal. If Linux launched a terminal every time there was output to show, you'd have a graphical terminal open all the time.

---

