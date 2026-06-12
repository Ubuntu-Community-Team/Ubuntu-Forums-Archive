---
title: "Screen Resolution"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Dfnoboy on 2007-06-16
Right now I can only run 1024x720, which is killer on my eyes.
When I try to run 800x600, the display is scrambled and eventually it resets to the old resolution.

Please help =D

---

### Post by Dfnoboy on 2007-06-16
no help? ahahaha =(

---

### Post by RichPicker on 2007-06-16
Will this help?
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by Dfnoboy on 2007-06-16
Where do I go type all that in? o.o

---

### Post by blue_shift on 2007-06-16
the terminal - gnome-terminal if you're on ubuntu, konsole if you're on kubuntu.

---

### Post by RichPicker on 2007-06-16
You should be able to just click the link. It's a URL.
Or go to wiki.ubuntu.com and do a search for Screen Resolution
Sorry to give links to web pages, but the instructions are there.

---

### Post by drascus on 2007-06-16
Hey check this program out I think there is even a Ubuntu Wiki about it. Its a GUI that will let you identify and modify your screen resolution automatically. Its a snap and there is no typing in the command line required. 
[http://http://www.cyskat.de/dee/progxorg.php]("http://http://www.cyskat.de/dee/progxorg.php")

---

### Post by Dfnoboy on 2007-06-16
it's a dead link, Drascus.

---

### Post by Golyadkin on 2007-06-16
Just remove the first http:// part: [here]("www.cyskat.de/dee/progxorg.php")

---

### Post by skymera on 2007-06-16
this might seem the answer to everything but....

```
 sudo dpkg-reconfigure xserver-xorg 
```

if your Intel you CAN use this

```
 sudo apt-get install xserver-xorg-video-intel 
```

---

### Post by drascus on 2007-06-16
Sorry about the bad link thanks for the fix.

---

### Post by Golyadkin on 2007-06-17
No problem, it seems to be some kind of bug in the forum. Because when I pasted the entire link with http:// into the "Insert Link" dialog, it doubled the http:// part for me too, so I had to edit it. Now it seems to work fine again.

---

