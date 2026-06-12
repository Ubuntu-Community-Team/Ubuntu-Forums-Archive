---
title: "Cannot close CD Drive with keyboard"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by nachomania on 2007-11-19
Hello. As is obvious, I am a beginner. Getting all of my preferences in has been pretty easy, with the exception of my CD drive. I have a button on my keyboard which is assigned to eject the drive. It does this perfectly; the only problem is that it doesn't go back in when I press the button again. Would there be some way to get my CD Drive to first take "eject", and then "eject -t" after? Thanking in advance

---

### Post by Dr Small on 2007-11-19
A bash script would do it, but I do not know how I would get a keyboard shortcut to run a bash script...

---

### Post by dpar on 2007-11-19
According to > man eject, not all devices support the -t option. Are you sure yours does?

---

### Post by nachomania on 2007-11-22
Yes, I've tried it in Terminal.

---

