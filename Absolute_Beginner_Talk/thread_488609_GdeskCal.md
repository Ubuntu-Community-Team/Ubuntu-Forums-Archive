---
title: "GdeskCal"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-06-30
where does this install to? I downloaded via synaptic but can not find it under my applications.

---

### Post by p_quarles on 2007-06-30
I don't use that one, but you should be able to find it one of two ways:

1) Right click on "Applications", select "Edit Menus", and then find the application and make sure the box next to it is checked. 

2) Right click on one of your panels, select "Add to Panel," and look through the options to see if you can add an applet for GdeskCal.

---

### Post by Obor on 2007-06-30
have you tried 
```
whereis gdeskcal

``` in the terminal (that should find where its installed. Also try launch it with Alt-F2 and gdeskcal

---

### Post by jba6511 on 2007-06-30
I get the following from running whereis

[PHP]blake@e6300:~$ whereis gdeskcal
gdeskcal: /usr/bin/gdeskcal /usr/X11R6/bin/gdeskcal /usr/bin/X11/gdeskcal /usr/share/gdeskcal /usr/share/man/man1/gdeskcal.1.gz
blake@e6300:~$ 
[/PHP]

It is not in the applications at all when I go to edit them. Running gdeskcal in terminal does not launch the program either. How do I get this thing to start to see if I like it?

---

### Post by Obor on 2007-06-30
you can edit menus and add /usr/bin/gdeskcal find some icon or create a launcher for /usr/bin/gdeskcal
it should run in the terminal as well with the patth/to/where/it/is ( /usr/bin/gdeskcal )

---

### Post by jba6511 on 2007-06-30
thanks. got it working now

---

