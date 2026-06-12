---
title: "Windows loading funny.... Very randomly...."
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by ts51 on 2007-06-16
I've been using beryl for a while, and just recently, windows will often load with nothing in them but tan, or tan with white boxes. Also, some times when I go into menus the text isn't highlighted as it usually is. 

How can I resolve this, and is it a Beryl problem as I suspect (If I have to part with beryl, I don't know what I'll do!)

Please help me out,
ts51

---

### Post by ts51 on 2007-06-16
Just re-read my post, and incase it's not clear, I'm talking about the windows in Ubuntu, not the operating system.....

---

### Post by skymera on 2007-06-16
u sure you got the setting scorrect?

---

### Post by ts51 on 2007-06-16
Yeah, I hardly mess w/ them. Plus, what settings would possibly "load blank windows" or "only highlight menus sometimes" ? :)

---

### Post by testube_babies on 2007-06-16
Beryl-Manager icon -> Advanced Beryl Options -> Rendering Platform -> Force AIGLX fixed the blank window problem for me (on nVidia)

---

### Post by bone43 on 2007-06-16
> **ts51 said:**
> I've been using beryl for a while, and just recently, windows will often load with nothing in them but tan, or tan with white boxes. Also, some times when I go into menus the text isn't highlighted as it usually is. 

How can I resolve this, and is it a Beryl problem as I suspect (If I have to part with beryl, I don't know what I'll do!)

Please help me out,
ts51

Try right clicking on the Beryl icon and hit> Reload Windows Manager, I some times have this problem after a long uptime and this fixs it.

---

### Post by ts51 on 2007-06-16
> **testube_babies said:**
> Beryl-Manager icon -> Advanced Beryl Options -> Rendering Platform -> Force AIGLX fixed the blank window problem for me (on nVidia)


I did this, and now after I log in, I don't see anything except a giant file system and blank panels! Can move, mouse but can't do anything!! What do I do??? I need to make beryl stop loading without actually logging in! What do I do? 

Please Help As Soon As Possible!

-ts51


Did I ruin my Ubuntu?? :sad:

---

### Post by ts51 on 2007-06-16
Does anyone know what to do? 

As of right now 1/3 of my HD has Ubuntu living on it, and I can't even get it to work

---

### Post by testube_babies on 2007-06-16
Sorry about that...apparently that won't solve your problem :)

To fix it:

CTRL+ALT+F1

then login and type killall beryl

CTRL+ALT+F7 to return to gnome

Then you can deselect Force AIGLX from the menu and reload beryl.

---

