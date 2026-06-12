---
title: "Java Application Error"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by PlasticWorm on 2007-05-29
Hello,

A long while back, I got my wireless working. Recently I've been trying to get this java application to run:

[www.illarion.org](www.illarion.org)

When I load it up and start it states:
"Unable to find requested screen display mode"

I have tried to run in different settings as well. Fullscreen, windowed, 16/24/32 bit, and such.

I have java runtime 1.6 and an ati x1800xt (not sure if that helps). I cannot seem to find the problem, or a relating problem. Thanks for your help.

---

### Post by kernel tom on 2007-05-29
never used the application before, but a lot of times the problem is with your java paths...

to ensure your java is not causing the problem run this in the terminal

sudo update-alternatives

this will bring up piecewise most of your default paths including your java paths, just hit return to keep the path current, or if you see a path thats wrong and see a java6 option, select it by entering the appropriate number.

hope that helps a little

---

