---
title: "Avant Window Navigator Troubles?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by zombiepkx on 2007-03-08
This is what happens when I open it:
[IMG]http://img507.imageshack.us/img507/2874/screenshot1ve5.png[/IMG]

Part of my screen goes black, and it looks weird and such. In terminal it gives me this:
```
(avant-window-navigator:7894): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed

(avant-window-navigator:7894): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed

```

Loads of fun, I guess.
Solutions?

---

### Post by zombiepkx on 2007-03-08
Mrrrrrrrr help.

---

### Post by zombiepkx on 2007-03-08
bump. x.x

---

### Post by zombiepkx on 2007-03-08
Help please.

---

### Post by zombiepkx on 2007-03-08
Nobody's helping me because I made fun of WoW, is that it?!

---

### Post by Quicksand on 2007-03-08
Nobody's helping because it has only been two hours since your first post!  Patience . . . patience . . .

Are you running a compositing window manager (e.g. beryl or compiz)?  You need that for awn to work.

---

### Post by zombiepkx on 2007-03-08
Haha, thanks for the response - I am very impatient, I fixed it, I had to update a few libraries and unistall/reinstall beryl. Found out it's not worth it anyways, since beryl is just not my kinda window manager (I enjoy Metacity / defaults, smooth running, no resources needed, and simple. :P)

Onto my next problem!

---

### Post by hoyaabc on 2007-03-08
how did u fix it? I got same problem.

---

### Post by jpointer on 2007-05-08
My AWN does that when I do not have beryl open, do you have beryl installed I don't think its required but it might have something to do with it.

---

### Post by macabro22 on 2007-05-20
> My AWN does that when I do not have beryl open, do you have beryl installed I don't think its required but it might have something to do with it.
Reply With Quote

Wrong. Beryl IS required. The black stripe is likely due to beryl not being loaded as the window manager. Thats my experience at least.

---

### Post by Ziox on 2007-05-20
I can confirm that AWN indeed need a window manager that can handle desktop composite, such as Beryl and Compiz.

---

