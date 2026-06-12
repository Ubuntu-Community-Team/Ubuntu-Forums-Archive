---
title: "Ubuntu Cube"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by chemicalgr on 2008-03-16
What are the system requirements in order to run in   Ubuntu "Cube mode"?
Is it really helpfull or it's just another fancy application?

---

### Post by herbster on 2008-03-16
"Cube mode" is actually a window manager called Compiz Fusion. The requirements are really a video card that can handle 3D acceleration, it doesn't ask for much to run decently.

It's helpful and fancy in many folks' view, but that question is entirely subjective and for you to discover once you are using it.

---

### Post by Jerry N on 2008-03-16
I played with the Compiz Fusion stuff including the cube for a while right after Gutsy came out.  My opinion was "cute but so what".  I shut down all the"effects" and haven't been tempted to turn them back on even once in the last 4 months.  But then I am just a grouchy old f*rt.

Jerry

---

### Post by chemicalgr on 2008-03-17
I've tried it once but whith beryl if i remember correct ,but it didn't work and caused unstable condition to my system,i have not tried again since then ,thoughting that this thing(cube) isn't for my pc's abilities (P4,Nvidia FX5200 128Mb,RAM 768Mb).
I'll try again.

---

### Post by vishzilla on 2008-03-17
In the terminal enter ```
glxinfo | grep render
``` if the result is 'direct rendering: yes', your video card supports 3D rendering

---

### Post by bwang on 2008-03-17
Compiz is rather picky and will only run on newer Nvidia, ATI, and Intel video cards/chipsets (so for example it will not run on the Nvidia RIVA TNT2 or the S3 Savage)

---

