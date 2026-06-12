---
title: "problem compaq armada 1700 laptop vga"
date: 2005-06-10
forum: Absolute Beginner Talk
---

### Post by janneman on 2005-06-10
hi,

i've got some vga problems with my compaq armada 1700

I can only choose 640*... resolution, i know this is normal, i tried al the stuff people suggested me, like kdtp sudo .... to reconfige the vga etc. but nothing worked.


i cant choose between other resolutions


is there a way out? using the name of another vga than what is in my laptop or something?



thx,


Jan

---

### Post by meat on 2005-06-10
I had the same problem and I had to edit the xorg.conf file to include higher resolutions.  This still did not fix it until I edited the horizontal and vertical refresh rates.  The listings in my xorg.conf file were different from the actual manufacturers specs.

---

