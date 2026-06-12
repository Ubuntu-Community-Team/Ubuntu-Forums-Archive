---
title: "Vertical Screen"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by blk03mitsues on 2007-05-10
how can i configure my screen so that it is vertical instead of horizontal? so that instead of being 1024x768 its 768x1024, i might find the need to rotate my screen 90 degrees for the current case mod i'm doing. thank you

---

### Post by Seanuntu on 2007-05-10
System --> Preferences --> Screen Resolution --> Rotation

[http://ubuntuforums.org/showthread.php?t=439190](http://ubuntuforums.org/showthread.php?t=439190)

---

### Post by blk03mitsues on 2007-05-10
this works on all ubuntus? i got xubuntu 7

---

### Post by blk03mitsues on 2007-05-11
screen resolution preferences
Defaul settings

Resolution:1024x768
refresh rate: 60hz

options
make default for this computer only


help close apply


thats all i see when i go into screen resolution

---

### Post by blk03mitsues on 2007-05-12
bump?

---

### Post by heimo on 2007-05-12
In Feisty, I do see Rotation option under Screen Resolution Preferences. For me it's grayed out, disabled as my card and/or drivers don't support it.  If your card supports it, you could use xrandr on command line to rotate screen.  Run it without parameters to find what options you have (I'm not sure if this program is available in Dapper).

```
xrandr
```Outputs at the end:
```
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none

```You can see xrandr syntax by typing:
```
xrandr --help
```You could try
```
xrandr -o 0
xrandr -o 1
xrandr -o 2
xrandr -o 3
```

---

### Post by blk03mitsues on 2007-05-14
well......you say it shows but it might be disabled because of your card/drivers.......... so if mine support the rotation then why would i need the code?:confused:  is it for in case my card/drivers allow it but i dont get an option anywhere.......btw i dont have a vid card...

---

### Post by heimo on 2007-05-14
> **blk03mitsues said:**
> well......you say it shows but it might be disabled because of your card/drivers.......... so if mine support the rotation then why would i need the code?:confused:  is it for in case my card/drivers allow it but i dont get an option anywhere.......btw i dont have a vid card...

Uh. Ok. You can check if rotating is possible at the moment and do it by using xrandr. If it's not possible - it may need configuring or it may be impossible (because of lack of support in video card or its drivers). With video card I refer to both cards and integrated video devices.

---

### Post by blk03mitsues on 2007-05-14
thank you i'll look into it as i didnt bring the pc to work......

---

