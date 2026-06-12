---
title: "Installing seems to be imposible for me"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by slayer04 on 2007-07-10
Ok I am trying to install a program on ubuntu but for some reason I can't also I don't really know what I am doing if u want to know what the program is I am tring to install [http://www.geocities.com/peter_bone_uk/pivot.html](http://www.geocities.com/peter_bone_uk/pivot.html) there you go, I also downloaded the it from that site but in general I need to learn how to install programs in ubuntu I tried the most direct rout which was applications > add/remove programs but no luck I also tried the system manger but no luck there either. I did search the forums and did look for learning ways on my own but nothing I have tried so for has done any good :-({|=

---

### Post by charles.g.moore on 2007-07-10
is this a program that is compatible or written for Linux???

---

### Post by benmarvin on 2007-07-10
The software is for Windows, that's the first part of the issue. You may have success trying to install it under Wine.

---

### Post by Inxsible on 2007-07-10
> **slayer04 said:**
> Ok I am trying to install a program on ubuntu but for some reason I can't also I don't really know what I am doing if u want to know what the program is I am tring to install [http://www.geocities.com/peter_bone_uk/pivot.html](http://www.geocities.com/peter_bone_uk/pivot.html) there you go, I also downloaded the it from that site but in general I need to learn how to install programs in ubuntu I tried the most direct rout which was applications > add/remove programs but no luck I also tried the system manger but no luck there either. I did search the forums and did look for learning ways on my own but nothing I have tried so for has done any good :-({|=

First of, do you know if the software is Linux compatible ?

if not, you would have to use Wine to install it.

EDIT : Crap!! I type too slow :rolleyes:

---

### Post by regomodo on 2007-07-10
your basic understanding of linux is missing. Linux, natively, cannot install .exe's. You can try to install wine for that but i doubt you'll know how to do that. Then there's a chance that won't work (this little app should)

Do a little reading first

---

### Post by benmarvin on 2007-07-10
Perhaps there is a similar program already native to Linux.

---

### Post by slayer04 on 2007-07-11
](*,)of course wine, man there is a reason people call me slow but I looked into wine a little before 1: I would have no clue how to get that running/installed but I have heard isn't there a chance of completely running the system with wine??and yeah the program is not Linux native so it's another thing I forgot to even think about](*,) this just proves the theory of look before you leep

---

### Post by bodhi.zazen on 2007-07-11
> **slayer04 said:**
> ](*,)of course wine, man there is a reason people call me slow but I looked into wine a little before 1: I would have no clue how to get that running/installed but I have heard isn't there a chance of completely running the system with wine??and yeah the program is not Linux native so it's another thing I forgot to even think about](*,) this just proves the theory of look before you leep

LOL

No, wine will not "ruin your system".

[http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by 3rdalbum on 2007-07-11
Wine is very easy to install.

```
sudo apt-get install wine
```

then in the terminal, type "wine " and then drag the Windows program's installer to the terminal. Switch back to the terminal and hit Enter.

Installed Windows programs go into your home directory, under the hidden .wine folder. For instance, /home/slayer04/.wine/drive_c/Program\ Files/Pivot/pivot.exe. You can view hidden files and folders by going to the view menu on the file browser and choosing "Show Hidden Files".

As far as I know, Wine cannot ruin your system, although in some rare situations it can crash X, which doesn't do any damage to the system.

---

### Post by slayer04 on 2007-07-11
I don't know with my lack of knowledge I am liable to screw something up just like when I tried to make a dual boot system...but you guys convinced me I will try to install but I will have to do my home work before doing so so or I am going so be back here within the week..any how 


Thanks For All The Help =D>

---

