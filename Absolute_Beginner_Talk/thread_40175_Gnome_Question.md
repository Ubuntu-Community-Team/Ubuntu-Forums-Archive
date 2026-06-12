---
title: "Gnome Question"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by echokilo on 2005-06-08
When I close a window in Gnome, there is a black box that slowly shrinks. How do I turn this off? I looked in Window Behavior, but could not find anything.

---

### Post by 23meg on 2005-06-08
i'd be interested to know how to do this as well.

---

### Post by Sionide on 2005-06-08
Do you mean close a window, or just minimise one?

---

### Post by GrumpySimon on 2005-06-08
Have a look at [this thread](http://ubuntuforums.org/showthread.php?t=20610&goto=nextoldest).

It's not as easy as just turning it off, but you can get rid of it by checking the reduced resources flag.

Open a terminal and do this:
gconftool-2 -t bool -s /apps/metacity/general/reduced_resources true

--Simon

---

### Post by echokilo on 2005-06-08
No Change. :(

---

### Post by echokilo on 2005-06-09
Five bucks to the firts person who knows how to turn it off! :)

---

### Post by GrumpySimon on 2005-06-09
Cutting and pasting this line:
gconftool-2 -t bool -s /apps/metacity/general/reduced_resources true

into the terminal works for me (Immediately too). Easily turn it back on by:
gconftool-2 -t bool -s /apps/metacity/general/reduced_resources false

Btw: feel free to send the $5 [here](http://ubuntuforums.org/donationstotal.php) :)

--Simon

---

### Post by echokilo on 2005-06-09
That worked! 

And as promised, I donated the $5 as well.

---

### Post by GrumpySimon on 2005-06-09
Good for you :)

--Simon

---

