---
title: "Screen resolution stuck at 640x480"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by duchednier on 2007-04-11
-resolution is stuck at 640 x 480 and there are no other options on the resolution window-
I've searched all over the ubuntu forums, and while i have found tons of people with the same problem, none of them help me because the ubuntu information thingy (i seriously dont know what its called (the thing where you go into a terminal and get all the ubuntu .. stuff...)) is for their information, not mine, so i cant really use it (beleive me i've tried, i had to reinstall ubuntu)
anywho, yeah i just switched from windows and dont know anything about this, im using ubuntu 6.06 
thanks for your time^^

---

### Post by bobplano on 2007-04-11
have you tried 
```
sudo dpkg-reconfigure xserver-xorg
```
yet?
it sounds like the thing you are talking about is the file xorg.conf and the reason people ask you to post that is to get information about your graphics card and drivers so if you would also post that then people can help you too. (I can't understand it much myself so someone else will have to read it over

---

### Post by duchednier on 2007-04-11
thanks, i did this, and it now says "please enter the video cards bus identifyer"
and then below it
 PCI:1:5:0__________ <----- thats where i'm supposed to write something

whats a bus identifyer and how do i find it?

---

### Post by bobplano on 2007-04-11
type in the terminal
```
lspci -X
```
and it will list all this stuff. find the one where it says your graphic card name and/or company and those are the numbers you need to have where it asks for it. you shouldn't have to add anything to it. if you really can't figure out which bus identifier it is then you can post the output of the command above here

---

### Post by duchednier on 2007-04-11
yaaaay!! i got it:D
thanks so much boplano for that first code, i basically just ended up pressing next about a thousand times, but it works and now i can see what i'm doing :D

---

### Post by andstuff on 2007-04-11
Actually, one can get around this by using the "safe graphics mode" on the live CD, at least it did for me. For the next person who'll be using the search button, not that it's much easier than changing stuff in xorg.conf or running the "lspci -X" setup thingy.

---

