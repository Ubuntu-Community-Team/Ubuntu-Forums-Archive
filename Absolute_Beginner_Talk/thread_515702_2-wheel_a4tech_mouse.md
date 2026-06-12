---
title: "2-wheel a4tech mouse"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by medya on 2007-08-02
hey
I just bought a 2-wheel mouse  (one wheel for up/down and one for right/left)

but in ubuntu the left/right scroll works like up/down.

any idea ? 

here is the products webpage:
[http://www.a4tech.com/en/product2.asp?CID=123&SCID=126&MNO=X5-35WD](http://www.a4tech.com/en/product2.asp?CID=123&SCID=126&MNO=X5-35WD)

---

### Post by asmoore82 on 2007-08-02
open your xorg.conf file with root(admin) priviledge:
open a terminal and ...

```
~$ gksudo gedit /etc/X11/xorg.conf
```

find the line that looks like this:
```
        Option      "ZAxisMapping" "4 5"
```
and change it to this:
```
        Option      "ZAxisMapping" "4 5 6 7"
```

you will need to restart X11 for the change to take effect;
restarting the whole computer is the simplest way to do this.

-OR-
logout and log back in to a failsafe term session and ...
```
~ $ sudo /etc/init.d/gdm restart
```

---

### Post by medya on 2007-08-02
hey thanks for reply, but it doenst work, nothing happens after I add this and restart it .
> 
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

by the way as u see above it says
Emulate3Buttons
my mouse is 5 buttons shouldnt I change that?

---

### Post by medya on 2007-08-02
bump

---

### Post by asmoore82 on 2007-08-02
you can remove the Emulate3Buttons line completely if you want ...
Emulate3Buttons makes is so that left-clicking and right-clicking as the same time
produces a middle-click or wheel-click on modern mice

add this line right above the ZAxis  line

```
Option	"Buttons"	"7"
```

and restart X again ... now try all the buttons/wheels and see if anything does the horizontal scroll.

P.S. each wheel counts as 3 Buttons (Click, Down and Up)

---

### Post by medya on 2007-08-02
hey buddy I did it, no diffrent.

right/left scroll acts like up/down

---

### Post by asmoore82 on 2007-08-02
okay...
change the line
```
        Option      "Protocol" "ImPS/2"
```
to
```
        Option      "Protocol" "Auto"
```

and try, try, try again (restart X :D)

---

### Post by medya on 2007-08-03
no doesnt work after adding "atuo"  now the extra buttons dont work 
(the extra side bouttons used to work like middle and rick click)

and scroll buttons are still like before (both of them are up /down)

---

### Post by medya on 2007-08-03
I think the reason that side buttons stopped working was removing emulate3buttons .

btw where I can find all available options for mouse in the xorg.conf ?

---

### Post by medya on 2007-08-03
hey I changed the buttons to 9 , and it works fine now :)

---

