---
title: "Amarok 1.4.3 not loading at all"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by kkuzia on 2006-09-10
Hoping to find some help for a rather troublesome Amarok issue I am experiencing.  I did my best to search around in other locations for a solution, but to no avail.  So here goes...

I have previously been able to run Amarok 1.4.3 without an issue, but earlier this evening when attempting to run it... absolutely nothing happened.  I would click on the icon to load it, the start-up window with the Amarok logo would flash on the screen (for a split second) and then would disappear without the program ever loading.  I tried installing it... uninstalling... rebooting... etc.  I just cannot seem to figure out what went wrong.

Any ideas for walking a real Ubuntu newbie through a possible solution? :-k 

Thank ya kindly.

Kev

---

### Post by kkuzia on 2006-09-11
Umm... anyone? :D

---

### Post by Lord Illidan on 2006-09-11
Try running amarokapp from Konsole...see what it outputs.

---

### Post by kkuzia on 2006-09-11
> **Lord Illidan said:**
> Try running amarokapp from Konsole...see what it outputs.

I get the following when I run amarokapp from terminal:

amarokapp: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

Now, I know there was something related to a file with a similar name when I was trying to set up some XGL, as found here: [http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper)

Not sure if I should go back and try to undo what I did there (if I can even figure out HOW to do that.  lol)

---

### Post by Arevos on 2006-09-12
Try installing the libgl1-mesa package, either through synaptic or via the command line (sudo apt-get install libgl1-mesa).

---

