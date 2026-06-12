---
title: "Hey how to know wot is my graphics card ??"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by HARIHARA SUBRAHMANYAN on 2008-03-08
hey i want to kno wot s my graphics card ......wot s the command for it??sorry folks i am very new to linux......so just help me out.......

---

### Post by forestpixie on 2008-03-08
lspci |grep VGA

or 

lspci

---

### Post by Butthead on 2008-03-08
glxinfo always worked for me.

lspci sometimes returns a "unknown device" string. :confused:

---

