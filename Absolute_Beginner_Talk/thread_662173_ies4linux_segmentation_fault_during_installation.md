---
title: "ies4linux segmentation fault during installation"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by yellowband on 2008-01-08
hi

i'm trying to install ies4linux.  I have wine and caextract.  when i try to run ./ies4linux, i get the following error.

ui/pygtk/python-gtk.sh: line 6:  9286 Segmentation fault      (core dumped) python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py

Am i missing a library or something?

---

### Post by philinux on 2008-01-08
Once extracted open the folder and just double click ies4linux it's an executable file.

---

### Post by yellowband on 2008-01-08
?? i know, and when i execute it, i get the errors. 

has anybody had / solved this problem?

thanks

---

### Post by shareMenaPeace on 2008-01-08
Have a look here, bottom comments

[http://www.tatanka.com.br/ies4linux/news/41](http://www.tatanka.com.br/ies4linux/news/41)

---

### Post by yellowband on 2008-01-08
cool, thanks for the link, it solved my problem

in case anybody else it too lazy to click the link and read, the problem occurs when Adobe's website is down and the installer cant grab a copy of adobe flash player.  just deselect the option to install the flash player and the install should proceed.

---

### Post by mquick6 on 2008-01-13
I don't know if this helps.  At first I was getting a segmentation fault so I disabled flash and tried again and I  received another error.    I tried the automatic install with no gui and everything worked fine.

                       ./ies4linux --no-gui

---

### Post by Marco_Polo on 2008-01-20
Thanks mquick6 - I had the same issue with Gutsy.  The no gui option installed the browser, but I can't see my text in the address bar ...

---

### Post by andrewkk on 2008-01-30
> **mquick6 said:**
> I don't know if this helps.  At first I was getting a segmentation fault so I disabled flash and tried again and I  received another error.    I tried the automatic install with no gui and everything worked fine.

                       ./ies4linux --no-gui

After getting a segmentation fault with just ./ies4linux, this solution worked for me.

---

