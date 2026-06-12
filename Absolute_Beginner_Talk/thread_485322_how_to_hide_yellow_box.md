---
title: "how to hide yellow box"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2007-06-26
HI all.  I was wondering how do you remove the box that appears when your mouse is left hovering over a window or icon for a few seconds.  I have attached a screenshot so you guys know what I'm talking about.  Thanks.

---

### Post by Sushubh on 2007-06-26
using compiz/beryl?

---

### Post by Gen2ly on 2007-06-26
Thats a good question.  I'm curious to know this myself.  I imagine theres a way to turn it on and off in the Configuration Editor?  I searched 'hover and 'tip' but it didn't find anything.

---

### Post by 3rr0r on 2007-06-26
I want to hide the little yellow box, that way beryl is the only window popup thing that shows up.

---

### Post by 3rr0r on 2007-06-26
Look, this thing..

---

### Post by steveneddy on 2007-06-26
Just tell the little window previews to be on top, instead of the background. They will cover it up.

You can't get rid of them. They, the little yellow windows, are hard wired into Gnome. I have tried hacking it out, but it makes the tool bar functionality unusable. Crazy code there.

I want the same thing, but I am waiting for a newer version of Gnome to come along and give us the option to get rid of those ugly buggers.

---

### Post by Shazaam on 2007-06-26
Terminal> gconf-editor
Surf to apps-panel-global
untick tooltips-enabled.

---

### Post by 3rr0r on 2007-06-26
> **Shazaam said:**
> Terminal> gconf-editor
Surf to apps-panel-global
untick tooltips-enabled.

sorry but that doens't do it.  After I did that, I still have the tool tips.  I even restarted and checked the gconf-editor again just to be sure the changes stuck.

---

### Post by steveneddy on 2007-06-26
> **Shazaam said:**
> Terminal> gconf-editor
Surf to apps-panel-global
untick tooltips-enabled.

That only gets rid of the ones on the top panel, the ones that launch when you mouse over a shortcut.

---

