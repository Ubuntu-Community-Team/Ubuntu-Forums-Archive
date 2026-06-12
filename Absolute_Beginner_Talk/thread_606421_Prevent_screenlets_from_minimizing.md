---
title: "Prevent screenlets from minimizing?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Phristen on 2007-11-07
Ok, I know about the widget layer in compiz, but then my widgets will only be visible when I press F9, and I want them to be visible all the time. And not minimize when I press show desktop.


How?

---

### Post by mivo on 2007-11-07
In the CompizConfig Settings Manager enable the Widget Layer plugin. In the plugin's options go to the "Behaviour" tab and type in the names of the screenlets that you don't want to minimize, i.e. Flower.

In the Screenlet's options you need to UNcheck "Treat as Widget".

That's all. :)

---

### Post by Phristen on 2007-11-07
I typed "Flower" and launched one, but it is still getting minimized. So do the rest of them :confused:

P.S. Ok I've searched for it and it seems we should enter something like "name=FlowerScreenlet.py"... But that simply attaches the screenlet to the widget layer, regardless of whether the "Treat as widget" thing is turned on in the screenlet settings.

---

### Post by mivo on 2007-11-08
Hmm, I did what I wrote, and it worked with all of them. I only used their names, i.e. Flower , in the Widget Layer plugin, and that worked. :confused: Only after I unchecked the widget option in the screenlet, though.

---

### Post by Phristen on 2007-11-08
Ok, here's how I was able to do it.

In ccsm I set the background brightness level to 100% and unchecked the "end widget mode on click" checkbox. Now when I press F9 my background doesn't fade and I can still work with desktop items, while the widgets are visible. :)

---

### Post by Phristen on 2007-11-08
Here's another noob question about screenlets...
How do I prevent other windows from snapping to them?

---

