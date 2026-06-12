---
title: "[SOLVED] Help with keboards and mice"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Wildboar on 2008-01-10
I have just recently gotten my wireless working since I installed Gutsy and love it.  I am obviously very new to this but am not afraid to learn (at a reasonable pace).

  I have a Microsoft Natural Ergonomic Keyboard 4000 for Carpal Tunnel Syndrome and a Kensington (Wireless Mouse in a box).  Both of which I like very much in a "Gates" environment but would like to use some of the additional buttons (especially back and forward in Firefox).

  Though I hope to learn a lot about Ubuntu as time goes on, I've not been able to successfully activate the extra buttons on my mouse using the different threads I've found so far.  The keyboard has me a bit more intimidated since apparently there is some Kernel compiling that has to be done and for the life of me I can't figure what I was doing wrong at step 8.

  Has anyone already done the leg work so I can get them running without freaking me out too much while I learn at a more relaxed pace?

  While I have you, any suggestions for good Unix/Linux/Ubuntu books.  I used to do some Admin and DB management in a bastardized (by the Navy) version of Unix years ago but have forgotten most of it.

Thanks.

---

### Post by FreewheelinFrank on 2008-01-10
This worked for me and my mouse:

[http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

Using the mouse autodetection evdev configuration

[http://ubuntuforums.org/showpost.php?p=3876272&postcount=586](http://ubuntuforums.org/showpost.php?p=3876272&postcount=586)

In 'Section 2: Side buttons and Nautilus, Epiphany, Konqueror, etc (Optional)'  you may need to change the button numbers for your mouse. Use Xev to determine the output from the buttons on your mouse and modify accordingly.

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
```

Change b:6 and b:7 to what Xev tells you are the button numbers fro the forward/backward buttons on your mouse.

---

### Post by Wildboar on 2008-01-10
Sweet, Mouse problem solved.  You rock...

---

