---
title: "Expose-like effect without 3D acceleration"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by meuge on 2007-06-15
I am tired of dealing with the poor responsiveness of Beryl, and the fact that it crashes when I use a specialized app (tclkit-based) that I cannot do without. 

(Yes, I know it's not their fault that ATI drivers require XGL because they don't support AIGLX. I've never experienced these issues on an Intel-graphics PC)

I am willing to give up all the pretty effects, but I really got used to the Scale plugin of Beryl. Is there anything out there that will give me a similar way to select windows graphically, but that I could run without XGL?

---

### Post by BarfBag on 2007-06-15
The Mandriva developers were working on simple desktop effects that didn't require 3D acceleration.  They actually looked useful.  For example, whenever you highlighted text, the window would peal back exposing what was behind it.  Looked pretty useful for copy and paste.  I'm not sure whether or not they went through with it.  I did a search (it was posted here), but can't find the link.

Other then that, you're stuck with XGL.

---

### Post by happy-and-lost on 2007-06-15
The Compiz, which is faster than Beryl anyway, that comes with Feisty supports an expose-type thing. Search for Compiz in synapnic, I think the "extra" and "gnome" compiz packages will give you a method of enabling it

---

### Post by starcraft.man on 2007-06-15
> **happy-and-lost said:**
> which is faster than Beryl anyway

Really? I never saw any speed difference and I've used both (and stuck with Beryl, i prefer its plugins).

As for OP, let me recommend a few tweaks to Beryl to get it to perform better.

Open the Beryl Settings Manager and go to General Options tab (it should be default). Now tweak things I list and you should see a bit more performance/stability (I actually crash less after I tweaked these and another thing):

Texture Filter > Fast
Level of Focus Stealing Prevention > None
Detect Refresh Rate > Uncheck (no x)
Refresh Rate > Set Manually to your screens rate.
Sync to Vblank > Uncheck

You should see things get better after that. I don't think it needs restart to take effect.

I don't know of an expose feature that isn't in compiz/beryl and works well... I hope that helps :).

---

