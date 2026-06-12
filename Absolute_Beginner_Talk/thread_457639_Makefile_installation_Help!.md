---
title: "Makefile installation Help!"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by izizzle on 2007-05-28
Hey Guys. Once again, I am having a noobish problem. I dont know how to run the makefile files. I downloaded Neverball for linux, and I dont know how to install it. Can anyone help?

//izizzle

---

### Post by taurus on 2007-05-28
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by izizzle on 2007-05-30
I tried the link. No help. I need EXTREMELY SPECIFIC step-by step directions on how to install a makefile.

please help, izizzle

---

### Post by mrgoodkat on 2007-11-13
Thank you Taurus, that link is absolutely BRILLIANT.

Also, the game mentioned is in the main repository!! One of the first things the instructions say is always check that. There you go! :D

---

### Post by meatpan on 2007-11-13
> **izizzle said:**
> I tried the link. No help. I need EXTREMELY SPECIFIC step-by step directions on how to install a makefile.

please help, izizzle

Make sure you have build tools installed.  Run: ```
dpkg -l build-essential 
```.  If you are missing the package, install it via ```
sudo apt-get install build-essential
```.  This should help you with a typical gnu/linux style make process.

If this doesn't work, post more information about what you are trying to make, and which commands you have attempted to run.

---

