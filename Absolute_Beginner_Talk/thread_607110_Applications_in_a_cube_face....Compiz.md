---
title: "Applications in a cube face....Compiz"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by minhamra on 2007-11-08
Hello All,
I would like to force an application to always open in a specific cube face.
I want my browser in face #1
Terminals to open in face #2
Nautilus(s) to open in face #3
various utils to open in face #4.

I would love to make this work but am I barking up the wrong tree?

---

### Post by srhlefty on 2007-11-14
Perhaps this is a long shot, but it's worth a try:

In Compiz you can set certain keybindings that make you jump to a specific face of the cube.  

Next figure out how to make linux think you pressed the key combination from a script.  A quick google located [xmacro]("http://packages.ubuntu.com/feisty/utils/xmacro")), which looks like it might be able to press the keys for you.

Finally, write a little wrapper script that executes the keyboard shortcut and then launches the program.  

You would have to have a separate one for each program that you wanted to open on a certain face, but once you've figured out one, the rest would be trivial.

---

### Post by minhamra on 2007-11-19
Thank you very much, a nice way to look at it.

---

