---
title: "WINE problem"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by krunked on 2008-03-26
Ok so i am trying to install wine and i dont really know how to do this. 

The winehq site told me to copy and paste 

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list 

Into my systems list of APT sources but i dont know how to do that.

I know after i do that i have to use sypatico or w/e its called to install it.

Also i need flashplayer and i was wondering how i install it. I DLed it and extracted it to my desktop then opened it up and clicked on the install one and told it to run in both a terminal and just run but it wouldnt,

Thanx

---

### Post by krunked on 2008-03-26
O sry i am using the 64 bit 7.10 version of ubuntu

---

### Post by krunked on 2008-03-26
Ok so i just found where to put 

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

But it wont let me put it in o0

---

### Post by Darganot on 2008-03-26
Try these:

[http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644)

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins)

---

### Post by krunked on 2008-03-26
Ok for the flash player one i get this message

E: Couldn't find package flahsplugin-nonfree

and for the wine when i try to go into wine config it says it does not exist

and i also cannot fine the wine folder

---

### Post by Darganot on 2008-03-26
Have you changed your sources.list and added the gpg keys (the line you originally posted)?  You also need to make sure you run an apt-get update after you change this.

---

### Post by krunked on 2008-03-26
ok i just added it and how do i check if i run of a apt-get ( i JUST installed ubuntu if you couldnt tell)

---

### Post by Darganot on 2008-03-26
I'm not sure what you're asking, just run the apt-get line in the terminal to install the program (yep, that's all you need to do :)).  You should see the program download and install.

---

