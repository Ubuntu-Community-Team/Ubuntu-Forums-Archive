---
title: "X-Server needs a DISPLAY entry"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by fester225 on 2007-12-22
I'm trying to get a program running under WINE. When I do so I get,

"Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly."

I'm pretty sure X server is running, but there is no DISPLAY entry in Xorg.conf, and echo $DISPLAY gives ":0.0".

How do I get a DISPLAY entry in Xorg.conf?

---

### Post by nowshining on 2007-12-22
if u know the info. to put in the xorg.conf.  open up a terminal.

Applications - accesories - terminal

sudo gedit /etc/X11/xorg.conf

if u don't know report back. Once done, exit all apps and press ctrl + alt Del on the keyboard to logout and reset the x server.

---

### Post by fester225 on 2007-12-22
I don't know what's supposed to be there beyond needing a DISPLAY section. 

Do you have an example of a DISPLAY section along with what I should put in it?

---

### Post by nowshining on 2007-12-23
what exactly is the program?

---

### Post by fester225 on 2007-12-23
It's not a program, it's a configuration file for X-server. (Xorg.conf)

---

### Post by nowshining on 2007-12-23
no no, what program are u trying to install under Wine?

---

### Post by fester225 on 2007-12-23
World of Warcraft  at the moment.

---

