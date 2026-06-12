---
title: "arabic keyboard layout"
date: 2007-11-01
forum: Apple Intel Users
---

### Post by yousufinternet on 2007-11-01
hello every body i am planning to install ubuntu on my MacBook 
the problem is that ubuntu don't have arabic-mac keyboard layout 
becuase the keyboard layout is different than pc, so is their any way 
to add arabic mac keyboard layout or that is impossible :( .
thanks any way

---

### Post by cyberdork33 on 2007-11-01
I just looked in the keyboard option in gnome, and you could choose the 'Apple Laptop' keyboard, and then choose arabic layout. I don't know if it works or not, but it looked like the option was there.

---

### Post by yousufinternet on 2007-11-03
Unfortunately i have tried this already but it does not work
thank you any way

---

### Post by yousufinternet on 2007-11-17
up up 
i have installed ubuntu 7.10 on my apple  laptop 
so i only need to solve this problem 
and i will be very thankful to any 1 can help me

---

### Post by yousufinternet on 2007-11-24
up up

---

### Post by yousufinternet on 2007-12-03
ok is there any way i can make my own keyboard layout 
please help me with this

---

### Post by cyberdork33 on 2007-12-03
Have a look at the layout files in /usr/share/X11/xkb/symbols/macintosh_vndr

You may get better help with this in a different forum since it is not REALLY a Mac issue, it is just a keyboard issue. (Granted, it is a Mac keyboard, but it could be any keyboard... It doesn't make a difference that Apple made it.)

---

### Post by yousufinternet on 2007-12-04
the problem is the places of the arabic letters is different than the qwerty layout 
thanks for the path and i will try to solve the problem 
or buy an external keyboard :)

---

### Post by yousufinternet on 2007-12-29
hello every body 
thank u very much cyberdork33 for your help after searching in google i found [this guide]("http://www.linux.com/articles/113715") that teach u step by step how to create your own keyboad layout and i created Arabic mac keyboard layout it was very easy, the new keyboard layout can be downloaded from the attachments download it to the desktop,exract the archive and run this command :popcorn: :

> cd Desktop
sudo cp arm /etc/X11/xkb/symbols/ara 

the layout is not complete yet because it does not contain "harakat" 
i hope Arab mac users find the file useful :lolflag:

---

