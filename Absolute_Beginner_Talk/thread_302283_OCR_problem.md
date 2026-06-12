---
title: "OCR problem"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by quercusrobur2002 on 2006-11-18
Hi,I'm new to ubuntu - I just bought a new printer/scanner combo (HP PSC1510, works fine under Ubuntu, but when I tried to use the OCR feature under the Xsane image scanner program I got the error message as shown in the attached screenshot. 

Any help or advise as to how I can get OCR runing properly?

---

### Post by ametade on 2006-11-28
Hi,

That error means that you have to install gocr:
```
sudo apt-get install gocr gocr-gtk
```

---

