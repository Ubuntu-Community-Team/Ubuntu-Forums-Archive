---
title: "Reconfigure video"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Jormanks on 2007-03-21
I was trying to reconfigure my video card, to improve performance, but, today, the graphic interface doesn´t work again, probably because i messed up my configuration,

So, as  i must install (better, reconfigure) again... how can i do it ?

---

### Post by schwascore on 2007-03-21
What kind of card do you have and what steps have you already tried?

---

### Post by sad_iq on 2007-03-21
Try **sudo dpkg-reconfigure xserver-xorg** that should get you going !!!

---

### Post by Jormanks on 2007-03-21
Nop... it says something like Xserver is broken.
The thing is that I have a k8mm-v board, vt8237 chipset. Somehow i managed to find a thread in which explains how to "make" a driver for this video card. I have the thread, but in my ubuntu partition. I've searching and don't find it...

Anyway, i just have to reinstall the driver using only the terminal... and I'm.... well, I have no clue.

---

### Post by Jormanks on 2007-03-22
Seriously, some help would be great

---

### Post by schwascore on 2007-03-23
You should try searching the forums for your motherboard model.  I did and found several posts that at least provide some clues to the problem.  It seems as though your board does not agree with most kernel version, but I did find out that you probably have an ATI graphics card and will probably need their drivers.  Here is one of the posts:

[http://ubuntuforums.org/showthread.php?t=122181&highlight=k8mm](http://ubuntuforums.org/showthread.php?t=122181&highlight=k8mm)

Try providing more information with your request next time.  The more info you provide, the quicker you will get an answer.  Good luck and keep us posted.

---

