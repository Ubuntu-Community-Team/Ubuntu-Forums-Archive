---
title: "[SOLVED] Adjusting Volume resizes text in firefox!!!"
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by hanzomon4 on 2008-04-26
Using F4/F5 for adjusting the volume via pommed causes the text in websites to resize. I've tried making pommed require the fn key to activate the multimedia buttons but that doesn't fix the problem with firefox. I have a Macbook pro santa rosa, any ideas.....

---

### Post by McLeod Brennaman on 2008-04-26
My only guess would be to check keybindings in your compiz and gtk. Not sure what firefox uses as the shortcut for resizing text, but my guess would be F4, as F5 is probably refresh. What is sounds like is a modifier is being placed on those, as since (if I recall correctly) 2.4.14 linux kernel?, keyboard hardware bindings override software bindings, and you have to use a modifier key to control software features. Though I may be getting that mixed up with the mactel kernels, it could be firmware-controlled. Either way, though it is admittedly irritating, you could always try remapping volume up/down to for instance F8/F9 or whatever suits your fancy.

---

### Post by hanzomon4 on 2008-04-29
Well it only affects Firefox so I doubt the problem lies anywhere beyond that. I've checked about:config but can't find anything and the menu bar shows the keybinding for text resize as ctrl+ or ctrl-.

---

### Post by hanzomon4 on 2008-05-19
I don't have a fix for this so I'm going to bump it back out into the wild... One last time\\:D/

---

### Post by russo.mic on 2008-05-19
in your address bar, type about:config.
Almost every shortcut can be changed here. I don't have firefox installed, as i've been using konqueror lately. 

see this page for more info on this topic.

[http://www.mozilla.org/unix/customizing.html#keys](http://www.mozilla.org/unix/customizing.html#keys)

Russo

---

### Post by hanzomon4 on 2008-05-19
Well that helps but it takes awy my ability to use keyboard short cuts. I've tried changing it to alt and meta, just won't work. I did notice however that this effects nautilus and gnome-terminal, maybe others. It appears as though my F keys are being interpreted as Ctrl+ and Ctrl-. If I could only find out why and fix it.

---

### Post by hanzomon4 on 2008-07-06
Well I installed the mactel kernel and now the problem is gone. Any idea what is done differently in the mactel kernel then in the stock ubuntu kernel?

---

### Post by cyberdork33 on 2008-07-08
> **hanzomon4 said:**
> Well I installed the mactel kernel and now the problem is gone. Any idea what is done differently in the mactel kernel then in the stock ubuntu kernel?
What "mactel kernel" do you refer to?

---

### Post by hanzomon4 on 2008-07-09
A special kernel complied with intel mac patches in the mactel ppa. It's outdated now and many of the patches have been moved into the main kernel I believe. But something done in that kernel, be it a patch or config option, fixes my problem. However, like I said, it's outdated and my isight camera doesn't work with it.

---

### Post by hanzomon4 on 2008-07-18
It was pommed!!! You don't need it in hardy, my keys work as they should without it.

---

