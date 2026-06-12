---
title: "Asus Netbook + Lubuntu = No external screen?"
date: 2012-05-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ericplana on 2012-05-27
Hello.

I,m from Barcelona and also new at this forum.

I have an *Asus Netbook Eee PC 1015PX* running under *Lubuntu 12.04*.

All is working fine and I,m very happy to have been changed to Linux.

But today I was trying to conect the Netbook to and external screen using the side RGB conector and no signal at all.

Pressing [Fn]+[F8] doesn't works and no idea how to send the screen signal to an externel screen.:(

Any help or recomendation?

Thanks

---

### Post by ericplana on 2012-05-28
Fantastic !!!

It was so simple to solve. Just install ARandR controller and play with it.
It makes very easy the configuration of the 2 screens. External Screen and Laptop screen.

You can use the 2 at the same time, just the external and turn off the laptop screen, use the same desktop on the 2 screens or make and extension...etc.
All is on your hands.

```
sudo apt-get install arandr
``` 

After installing, go to "Preferences Menu" and then ARandR.

More info at : [http://www.ubuntugeek.com/arandr-a-simple-visual-front-end-for-xrandr.html](http://www.ubuntugeek.com/arandr-a-simple-visual-front-end-for-xrandr.html)

[[img]http://s13.postimage.org/qboeyp44j/image.jpg[/img]](http://postimage.org/image/qboeyp44j/)

---

