---
title: "fluxbox on ubuntu"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by MkfIbK7a on 2007-01-07
if i install fluxbox on ubuntu will it overwrite gnome

i get this when i put it in

```
jon@albert:~$ sudo aptitude install fluxbox fluxconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  at-spi brltty festival festlex-cmu festlex-poslex festvox-kallpc16k gedit 
  gedit-common gnome-orca gnome-screensaver gnome-themes libatspi1.0-0 
  libbrlapi1 libestools1.2 libgnome-speech3 libxevie1 python-at-spi 
The following NEW packages will be installed:
  fluxbox fluxconf 
0 packages upgraded, 2 newly installed, 17 to remove and 0 not upgraded.
Need to get 956kB of archives. After unpacking 52.1MB will be freed.
Do you want to continue? [Y/n/?] 

```

is this ok should i remove all of these items?:confused:

---

### Post by ajmorris on 2007-01-07
No gnome will not be removed. Gnome will only be removed if ubuntu-desktop is being removed. But fluxbox may use gnome in the sense that you can't run the two window managers seperately, i am not sure though and i highly doubt it. There will most likely be both options at your GDM login screen.

---

### Post by ardvark71 on 2007-01-07
Hi wert...

I wouldn't. Removing gedit doesn't look like a good idea to me. 

Best Regards...

---

### Post by ajmorris on 2007-01-07
Gedit is not really needed. There are other applications to read you text files.


But why do you want fluxbox?

---

### Post by riven0 on 2007-01-07
Yeah, that sounds strange. Would it make a difference if you do it through apt-get?:

> sudo apt-get install fluxbox fluxconf

?

---

### Post by MkfIbK7a on 2007-01-07
> **riven0 said:**
> Yeah, that sounds strange. Would it make a difference if you do it through apt-get?:



?

wow, thx that helped when i did apt-get it didnt try to remove anything thx riven0:D

---

### Post by riven0 on 2007-01-07
Glad to help! :KS

---

### Post by MkfIbK7a on 2007-01-07
wow fluxbox is awsome! its super fast and looks good too!

---

### Post by ardvark71 on 2007-01-07
> **ajmorris said:**
> Gedit is not really needed. There are other applications to read you text files.

Ok...I thought it was fundamentally tied to Gnome.

---

### Post by MkfIbK7a on 2007-01-07
nah there is nano and mousepad and kate for example...

---

### Post by macogw on 2007-01-08
> **wert613 said:**
> nah there is nano and mousepad and kate for example...

and vim!

---

