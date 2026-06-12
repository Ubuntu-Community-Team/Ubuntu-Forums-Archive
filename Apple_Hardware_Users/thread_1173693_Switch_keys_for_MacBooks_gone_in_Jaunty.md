---
title: "Switch keys for MacBooks gone in Jaunty?"
date: 2009-05-30
forum: Apple Hardware Users
---

### Post by regebro on 2009-05-30
In Intrepid there was a setting under keyboard options to Switch two keys when you had MacBooks, as otherwise < and ' are switched around. In Jaunty this option seems to be gone.

Anyone know how to fix this issue in Jaunty?

---

### Post by regebro on 2009-05-30
Also, the instructions for flipping the mode of function buttonsm so that F11 becomes F11 and not volume, doens't work under Jaunty either, I just noticed.

---

### Post by Richardcavell on 2009-05-30
Mate,

Why don't you look into the xev and xmodmap commands?  You need to install them if you haven't already:

 sudo apt-get install xmodmap
 sudo apt-get install xev

Xev will allow you to detect keyboard codes, and xmodmap allows you to map them to particular symbols.

On my keyboard, I have mapped the command keys (open apple) as the middle mouse button, and my enter key is the right mouse button.  I'm sure you can solve your problem with xmodmap.

Richard

---

### Post by cyberdork33 on 2009-05-30
> **regebro said:**
> Also, the instructions for flipping the mode of function buttonsm so that F11 becomes F11 and not volume, doens't work under Jaunty either, I just noticed.
the method changed a little, but it still works:
[https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard)

---

### Post by Chrissss on 2009-06-03
I'm stuck with this issue too, the option is unfortunatelly gone...

---

### Post by Rog-Mahal on 2009-06-04
Bump to cyberdork's post (these options can still be enabled, check his link). Also, Keyboard Preferences > Layouts > Layout options now includes several of the classic Mac keyboard problems such as switching command key behaviour. Check there for other keys you might want toggled.

---

### Post by cyberdork33 on 2009-06-04
> **Rog-Mahal said:**
> Also, Keyboard Preferences > Layouts > Layout options now includes several of the classic Mac keyboard problems such as switching command key behaviour. 
Cool! did not see that!

---

