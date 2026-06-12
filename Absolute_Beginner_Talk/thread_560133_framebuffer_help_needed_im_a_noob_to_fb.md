---
title: "framebuffer help needed im a noob to fb"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by 900donuts on 2007-09-26
heres the deal i want to do this [http://ubuntuforums.org/showthread.php?t=387598](http://ubuntuforums.org/showthread.php?t=387598) while still being able to flip back and forth between super skinny no X and what I'm used to but im haveing problems with the frame buffer thing. how do i know? i ran links2 in graphic mode in X and then tried it in the console (Ctrl+Alt+F1) and got till this point 

(!) Direct/util : opening '/dev/fb0' and '/deb/fb/0' failed
-->no such file or directory

it said some other stuff above and below but i don't have time to enter it in by hand. please don't let this fall between the cracks! I'm probably not the only one with this problem

---

### Post by kerry_s on 2007-09-26
you just run> links2 -g google.com
links2 will find the fb you have installed and use the best one.

see here, if you get that permission problem-> [http://ubuntuforums.org/showthread.php?t=453667&highlight=links2+permission](http://ubuntuforums.org/showthread.php?t=453667&highlight=links2+permission)

---

### Post by 900donuts on 2007-09-26
the thread you pointed me to tells me how to fix a permision problem my problem is that my system does not seem to have a framebuffer device is what im guessing also adding a url didn't work

---

### Post by 900donuts on 2007-09-26
maybe this will help tell me what this means

(!)DirectFB/FBdev: use fbdev option or set framebuffer environment variable

---

### Post by kerry_s on 2007-09-26
try
**links2 -g -driver fbdev google.com**

---

### Post by 900donuts on 2007-09-26
im away from my computer now but i'll try it when i get home 

also whats the framebuffer environment variable?

---

### Post by 900donuts on 2007-10-01
i got the frame buffer working how do i resize the links 2 window like thing its two small for happypenguin.org

---

