---
title: "Fading effect"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2006-11-04
When i close a window that is open i see something like a fading effect some black lines 

Does someone no how to remove this effect???

---

### Post by jordanmthomas on 2006-11-04
Do you actually mean when you minimize a window?

If so, try this:  press Alt + F2
```
gconf-editor /apps/panel/global
```
There is a checkbox for enable_animations.
Uncheck it and see if this solves your problem.

---

### Post by fasoulas on 2006-11-04
> **jordanmthomas said:**
> Do you actually mean when you minimize a window?

If so, try this:  press Alt + F2
```
gconf-editor /apps/panel/global
```
There is a checkbox for enable_animations.
Uncheck it and see if this solves your problem.

This doesn't work
Any other suggestions??????

---

### Post by jordanmthomas on 2006-11-04
What didn't work about it?  
Maybe you could explain more about what you mean by the fading black lines.

---

### Post by fasoulas on 2006-11-04
> **jordanmthomas said:**
> What didn't work about it?  
Maybe you could explain more about what you mean by the fading black lines.

As you said when you minimize the window

I uncheck it i close the configuration editor and it still doesn't work

---

### Post by jordanmthomas on 2006-11-04
After unchecking it, you can either log out and back in or
run this in your Alt + F2 window
```
killall gnome-panel
```
I forgot that you may need to restart the panel to fix it.  When you kill the panel, it will restart itself after reloading its settings.  See if it works after that.

---

### Post by fasoulas on 2006-11-04
> **jordanmthomas said:**
> After unchecking it, you can either log out and back in or
run this in your Alt + F2 window
```
killall gnome-panel
```
I forgot that you may need to restart the panel to fix it.  When you kill the panel, it will restart itself after reloading its settings.  See if it works after that.

it still doesn't work

---

### Post by jordanmthomas on 2006-11-04
Well, I don't know then.
Off to bed for me.

---

