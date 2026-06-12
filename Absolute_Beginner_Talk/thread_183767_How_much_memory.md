---
title: "How much memory?"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by oldnumber11 on 2006-05-28
How do I determine the operating specs on my RAM in my computer. # of MB and speed.

---

### Post by colo on 2006-05-28
Size: `free -m`

---

### Post by oldnumber11 on 2006-05-28
What  about the speed? e.g., 100  MHz? How can I find that out?

---

### Post by araz on 2006-05-28
Try these commands:
dmesg |less or
cat /proc/meminfo

---

### Post by oldnumber11 on 2006-05-28
That did not seem to work. this has piqued my interest now. My real question is: I am looking to add memory and I have 2 128 MB sticks which operate a 100 MHz. How do I know this will work?[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

---

### Post by Stew2 on 2006-05-28
What is the make and model of your PC? With this info and google its ususally not too hard to figure out :)

---

