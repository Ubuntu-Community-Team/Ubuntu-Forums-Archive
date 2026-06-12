---
title: "Accessing Programs in Wine"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by thomasaaron on 2006-09-22
Small hang-up.

I installed wine. I downloaded a windows program to it. 

when I go to the terminal and type: 
wine home/thomasaaron/.wine/drive_c/Program Files/Just Basic v1.01/jbasic.exe   

I get an error. Essentially, it is not accepting /Program Files/as a directory, I think because of the space between Program and Files.

How do you get past this?

BTW: just typing: wine jbasic.exe does not work. Moving it to the system32 directory does not work either.

How can I complete the path to the .exe file despite the spaces?

Best,
Tom

---

### Post by compwiz18 on 2006-09-22
put quotes around the path, ie **wine "home/thomasaaron/.wine/drive_c/Program Files/Just Basic v1.01/jbasic.exe"**

EDIT:

try this one (I use a ~ instead of /home/thomasarron) **wine "~/.wine/drive_c/Program Files/Just Basic v1.01/jbasic.exe"**

---

### Post by thomasaaron on 2006-09-22
THanks. I'll give that a whack.

---

### Post by CatKiller on 2006-09-22
As an alternative to the quotes, spaces in filenames get "escaped" with a \. The way I deal with spaces is to make use of the command line's Tab-completion. So you only need to type ```
 wine .wi<tab>dr<tab>P<tab>J<tab>j<tab>
``` and all of the <tab>s will have filled in the path for you. If there's more than one way of completing the next part of the path, the computer will beep at you, and pressing Tab again will show you the alternatives.

---

