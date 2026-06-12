---
title: "IInstalled a new linux box(IamUsingFVWM)&amp;DEBIAN MENU disappearedonThisPCforAllUsers?"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-16
IInstalled a new linux box(IamUsingFVWM)&DEBIAN MENU disappearedonThisPCforAllUsers?

Does someone would know ?
  
Maybe the permissions with the Debian Menu ?
  
Thank you very much, 

Patrick

---

### Post by Kyral on 2005-11-16
Umm, spacing please?

If you installed it on a new PC, then the Debian Menu isn't installed at all

```
sudo apt-get install menus
``` (I think)

```
update-menus
```

---

### Post by patrick295767 on 2005-11-16
Hi kyrial, 

it's sayign packages not foudn ... 
I'll look in wiki.packages stuffs or debian.org ...
  
to be continued 

thanks again kyrial !!

---

### Post by Kyral on 2005-11-16
I made a typo

```
sudo apt-get install menu
```

---

### Post by patrick295767 on 2005-11-16
in debian.org 
```
ackage cl-menusystem

    * stable (devel): Common Lisp Menu System
      0.0.0+2003.09.19-2: all

Package wildmenus.bundle

    * stable (x11): Bundle for GNUstep applications to have a horizontal main menu
      0.06-4: alpha amd64 arm hppa i386 ia64 m68k mips mipsel powerpc s390 sparc


```
  
not great result...

---

### Post by Kyral on 2005-11-16
*points to his last post*

---

### Post by patrick295767 on 2005-11-16
oup's, menu  without 's' !!
  
I am progressing ... progress progress

---

### Post by patrick295767 on 2005-11-16
Youpi, it's working !!
  
soo, the code was:
```
apt-get install menu
update-menus

```
  
then, I restarted my fvwm
  
& I got it !!!!!!! this debian menu!!
  
Additional question:  
I installed crossover weagers for office apps
but It's not present in the debian menu
  Is it due to the fact that I installed crossvover first and then I installed after the apt-get install menus ??
  
thank you again for your wise replies kyrial !!!
  
Thx  & greetz from belgium

pat'

---

