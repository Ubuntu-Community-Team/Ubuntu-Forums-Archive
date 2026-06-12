---
title: "(GIMP) Removing a color channel from an image and &quot;rendering&quot; this?"
date: 2010-02-11
forum: Art &amp; Design
---

### Post by NinjaNumberNine on 2010-02-11
I have a rather large image I've been working on, and while playing around with channel visibility, I noticed that by making the blue channel invisible, the image concept flipped entirely and the new look was great. Problem is, I don't know of a way to actually "render" this, and still have all my 30 layers and 3 channels (R, G and B). Can someone help me please?

Thanks,

NinjaNumberNine

---

### Post by mcduck on 2010-02-11
One way to get that effect on all your layers is to add a new layer on top of everything, then fill that layer with the color you wish to remove and finally set that layer's blending mode to "Subtract".

Just make sure you use pure colors, #ff000 for red, #00ff00 for green or #0000ff for blue.

(of course you are free to try any colors you want to, but with these colors you get the same effect as if you had removed the corresponding color channel)

---

### Post by NinjaNumberNine on 2010-02-11
Thanks so much mcduck. That's exactly the effect I needed! I'm gonna post up the image in a minute.

Thanks! :D

---

