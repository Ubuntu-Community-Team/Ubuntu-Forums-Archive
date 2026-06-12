---
title: "PovRay won't render file (or maybe I'm just a noob)"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-04-22
I made a basic povray file as suggested by a tutorial:

// This is a simple red sphere

// first, the camera position
camera {
  location <2,5,-10>
  look_at <0,0,0>
}

// now, some light
light_source {
  <0,-10,0>
  color rgb <1,1,1>
}

// the sphere
sphere {
  <0,0,0>, 5
  pigment { color rgb <1,0,0> }
}


And saved it as test.pov in my home directory

Then in the terminal I typed:

povray -Itest.pov

It does a bunch of crap in the terminal and a windows pops up for about half a second and disappears before I can even see any rendered image.

Got any idea what's going on?

Also it complains about not being about to find the user config files or something.

---

### Post by mabelrxu on 2007-04-22
i don't understand why you need a -l in there ...

---

