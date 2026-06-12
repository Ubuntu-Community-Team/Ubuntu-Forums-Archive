---
title: "Trackpad Problem on Macbook Pro"
date: 2014-11-28
forum: Apple Hardware Users
---

### Post by kmand on 2014-11-28
I'm running Ubuntu 14.04 on a MacbookPro4,1. The  trackpad mostly works, but is too sensitive to 'selection'. In other words I'm forever activating links I don't intend to, and selecting areas of text that I'm just trying to scroll through.

Is there a way to improve the trackpad experience?

---

### Post by rican-linux on 2014-11-29
Take a look at this article it may help you


[http://ppcluddite.blogspot.com/2013/06/getting-usable-trackpad-on-aluminum.html?m=1](http://ppcluddite.blogspot.com/2013/06/getting-usable-trackpad-on-aluminum.html?m=1)

---

### Post by kmand on 2014-12-14
Thanks for the link. What I did learn is that I can list and change the synaptics parameters with the "synclient" command. As far as the actual values in that posting they are for a 2006 era powerbook and not close to the ones for a few year old macbook pro.

As I try to relate the misbehavior to the parameters, I'm really stuck.

Is anyone using the trackpad for scrolling on a macbook pro 15"? I would really benefit from a "synclient -l" if its working well.

---

### Post by este.el.paz on 2014-12-15
kmand:

This problem showed up in various flavors of LM on my MBPro and I posted several threads about it . . . the "synclient" thing was mentioned, but I didn't want to mess with it . . . .  The ****simplest**** solution was in the GUI, I'm not booted in linux right now, possibly it was disable tap to click, and check "Disable touchpad while typing" . . . .  What was a problem of the cursor jumping around independent of me touching it, highlighting and erasing text . . . was gone . . . .

e.e.p.

---

### Post by kmand on 2014-12-17
Disable tap to click did fix the problem I was having, but it also eliminates the way I got button 2 and 3 emulation (by click on corners of trackpad). The mac style shift+click-bar doesn't work either. How are you getting button 2 and 3 emulation?

---

### Post by este.el.paz on 2014-12-18
> **kmand said:**
> Disable tap to click did fix the problem I was having, but it also eliminates the way I got button 2 and 3 emulation (by click on corners of trackpad). The mac style shift+click-bar doesn't work either. How are you getting button 2 and 3 emulation?

@kmand:

Nothing is perfect in this world . . . and having less features on the trackpad is not something I was happy about either, but, it's either dive into the CLI and make mods that may or may not work depending on the translation from one machine to another . . . OR, have the joy and pain of a free operating system, one that is not native to Apple.  In terms of 2 and 3 button emulation . . . I use a mouse on my MBPro . . . .  I'm not sure what the "shift-click-bar" feature is . . . .  "We don't always get what we want . . . but, in linux we get only what we need . . . ."  : - )

e.e.p.

---

