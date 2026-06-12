---
title: "NEC 1880sx resolution problem"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Nigggo on 2007-11-29
I installed Ubuntu for the first time on my laptop one week ago and am really happy with it, so i want to install it also on my desktop pc.
But i have a problem. While starting the live cd ubuntu automatically adjusts the resolution so that my screen doesnt accept it an it only shoes flickering images moving through...
I tried to find any guides and found some which told to reconfigure xserver. i did so and then i tried to restart x but without success. the display errors still occur.
could you give me any hint how to solve the problem?
i also tried a open suse install dvd and this worked but i dont want to use 2 different disturbtions because i am completely new to linux and working with one is enough for beginning.

thx

---

### Post by Nigggo on 2007-11-30
after a very long period of try and error i found a solution.
i searched for the vertical and horizontal refreshmentrate, added them manually while reconfigurating the xserver and choose 1024x768. this was the highest resolution working.
after installation i configured nvidia drivers and selectet my screen profile manually and now everything works fine...

---

