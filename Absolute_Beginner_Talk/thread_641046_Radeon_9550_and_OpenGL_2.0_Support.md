---
title: "Radeon 9550 and OpenGL 2.0 Support?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by ObeseOgre on 2007-12-14
I've installed the ATI Radeon 9550 drivers and according to the openGL version string I think I should have openGL 2.0 support.

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550/X1050 Series
OpenGL version string: 2.0.6334 (8.34.8)

But when I try to use GLSL functions that are in openGL 2.0 in my program, they aren't found.  Does this mean I don't have openGL 2.0?

---

### Post by Stemp on 2007-12-15
I guess you need the  libgl1-mesa-.... packages

---

