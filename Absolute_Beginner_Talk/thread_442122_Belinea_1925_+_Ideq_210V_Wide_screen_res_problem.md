---
title: "Belinea 1925 + Ideq 210V Wide screen res problem"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Ammo on 2007-05-13
I'm a total n00b to all of this, and i've managed to get my wireless card working thanks to the help on this forum.

The problem is i can't get my Belinea 1925 S1W 19" widescreen into it's native res of 1440x900

i'm using the onboard graphics which is a VIA UniChrome 2D/3D Graphics with motion compensation apperently

Can anyone help me in the simplest terms possible and step by step as i don't know any of the things I need to type into the terminal to get information.

Thanks for any help

---

### Post by nonewmsgs on 2007-05-22
in a terminal 

sudo dpkg-reconfigure -phigh xserver-xorg

it will ask you to checkmark the resolutions you like.  make sure you check the native one and you should be straight.

---

### Post by nonewmsgs on 2007-05-22
oh and make sure for videodriver you select VIA.  good work on getting your wireless working.  it is the hardest thing i have found so far, so everything else will be easier.

---

### Post by daulex on 2007-10-02
edit: got it to work. thank you.

---

