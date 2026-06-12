---
title: "Botched app. installs"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Micro Rotors on 2006-01-28
I have a question,

When you try to install something and you get errors and want to abort the install I close the terminal thinking I am done, but in fact I am finding that my hard drive is getting smaller and smaller. How do I properly abort a botched install without leaving junk all over the place? 

Also how do I claim back my real estate that is full of the botched attempts? 

:confused: :confused: :confused:

---

### Post by cwaldbieser on 2006-01-28
[QUOTE=Micro Rotors]I have a question,

When you try to install something and you get errors and want to abort the install I close the terminal thinking I am done, but in fact I am finding that my hard drive is getting smaller and smaller. How do I properly abort a botched install without leaving junk all over the place? 

Also how do I claim back my real estate that is full of the botched attempts? 

:confused: :confused: :confused:[/QUOTE]
I am guessing you aborted after downloading the package files, and they are taking up the space.  You can clean this out using "apt-get clean" or "apt-get autoclean".  There is a difference between the two that I am not 100% clear on.  "clean" just clears out your entire cache, while autoclean tries to just clear out "useless" packages.  I would have to give some thought to what a "useless" package is, but I would hazzard to guess it means one that is obsolete.

---

