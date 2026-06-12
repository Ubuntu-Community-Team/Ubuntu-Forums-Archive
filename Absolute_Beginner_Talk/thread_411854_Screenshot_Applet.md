---
title: "Screenshot Applet"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Morbeo on 2007-04-17
[FONT=Georgia]I'm looking for an applet which captures the whole screen and outputs it into given format. gnome-screenshot is no use, because It shows a dialog and I want it to be automatic. Like a daemon :) .[/FONT]

---

### Post by HumanAnarchist on 2007-04-17
Use the "print screen" key on your keyboard to taka a screenshot of the whole desktop, or use "alt + print screen" to just take a screenshot of the active window. 

-ha-

---

### Post by aysiu on 2007-04-17
That still brings up the dialogue. It doesn't send the screenshot directly to a file.

---

### Post by RedSquirrel on 2007-04-17
Install **imagemagick**. (It's in the repos, and it might even be on your system already.)

Then, in a terminal, do:

```
import -help
```or 

```
man import
```to see all of the options.


Here's what I use for screenshots:

**whole desktop:**
```
import -pause 7 -window root screenshot-`date +%Y-%m-%d_%T`.jpg
```**pick a window:**
```
import -frame window-`date +%Y-%m-%d_%T`.jpg
```You can change the output file type just by changing the filename suffix (.jpg, .png, etc.).

---

### Post by kerry_s on 2007-04-17
I agree with RedSquirrel, imagemagick if you need to manipulate the image, like resize it or something.

If you just want dirt simple you can try scrot(sudo apt-get install scrot) it's really simple and the commands are shorter and easier to remember.

i use these->

import:
import -frame -resize 1024x768 `date +%T`.jpg
import -pause 5 -resize 1024x768 -window root `date +%T`.jpg 

scrot:
scrot %T.jpg
scrot -b -s %T.jpg
scrot -d 5 %T.jpg

---

### Post by Morbeo on 2007-04-18
Tanks a lot, I appreciate your help :D

---

### Post by chakkaradeep on 2007-04-18
> **Morbeo said:**
> [FONT=Georgia]I'm looking for an applet which captures the whole screen and outputs it into given format. gnome-screenshot is no use, because It shows a dialog and I want it to be automatic. Like a daemon :) .[/FONT]

Use the feature to take snapshot after *x* seconds my friend :D

---

