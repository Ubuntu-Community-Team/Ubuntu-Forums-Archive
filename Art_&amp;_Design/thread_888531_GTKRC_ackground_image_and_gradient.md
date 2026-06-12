---
title: "GTKRC: ackground image and gradient"
date: 2008-08-13
forum: Art &amp; Design
---

### Post by killerwhale65 on 2008-08-13
Hi,

I was wondering if and how i can use a background images where i would normally use

bg[NORMAL]= "#080808"

Or a gradient?

Thanks!

Matt

---

### Post by AJB2K3 on 2008-08-15
Its something like ```
bg[NORMAL]="./images/plain_bg_bot_toolbar.png"
```
Cant be exact as its been a long time but I proved to various groupes that it was possible on windows.
[http://ajb-2k3.deviantart.com/art/gimp-skin-1974965]("http://ajb-2k3.deviantart.com/art/gimp-skin-1974965")
[http://ajb-2k3.deviantart.com/art/Gimp-in-violet-13451835]("http://ajb-2k3.deviantart.com/art/Gimp-in-violet-13451835")

---

### Post by killerwhale65 on 2008-08-15
hi,

this seems not to work unfortunately.

---

### Post by geoken on 2008-08-15
Download a pixmap theme so you can see the basic syntax required to use an image for a certain widget.

note: You will not be able use a widget and change it's color to a gradient with a pixmap. You will need to redraw the entire widget. For example, if you wanted a button to have some gradient on it, you would need to redraw the entire button and use that with a pixmap engine.

---

### Post by AJB2K3 on 2008-08-15
> **killerwhale65 said:**
> hi,

this seems not to work unfortunately.
Nope your right, its more like
```
bg[NORMAL]file ="./images/plain_bg_bot_toolbar.png"
```
How ever this is quite heavy stuff.
Try learning the basic of gtk themes first.

---

### Post by killerwhale65 on 2008-08-16
thanks, will try!

---

