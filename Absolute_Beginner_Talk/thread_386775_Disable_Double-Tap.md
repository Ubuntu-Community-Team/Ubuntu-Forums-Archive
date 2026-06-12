---
title: "Disable Double-Tap"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by mlhudson on 2007-03-17
I could really use help getting my Toshiba Satellite M35 trackpad to cease the double-tap feature. I make mistakes all over the screen. The buttons are sufficient. I don't need this feature. Any advice?

As I looked through the forum this seemed to be a model specific issue...but I could be wrong about that.

Thanks.

---

### Post by oilchangeguy on 2007-03-17
try this
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by mlhudson on 2007-03-17
> **oilchangeguy said:**
> try this
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

This is a great tip for turning the whole touchpad off w/ a keyboard shortcut. But my real hope is that I can just turn the 'double-tap in place of a mouse-click' feature. I want to use the touchpad as the main mouse, just not have every jitter of my finger be recognized as a mouse-click.

Thanks for helping...are there any more helps for this?

---

### Post by oilchangeguy on 2007-03-17
ok, do what i did to locate the link in my other post. go to the search box in the upper right of the page and type, disable tapping. there are approx. 10 posts on the subject. you should be able to find an answer there.

---

### Post by mlhudson on 2007-03-17
Thanks!

---

### Post by Henry Rayker on 2007-03-17
I believe adding 
```
Option   "MaxTapTime"	"0"
```
to your xorg.conf in the synaptics portion of the file should do it.

Let me know.

---

### Post by kevinlyfellow on 2007-03-17
if you install qsynaptics, there are options on how it handles tapping (qsynaptics is a gui to configure touchpads)

---

