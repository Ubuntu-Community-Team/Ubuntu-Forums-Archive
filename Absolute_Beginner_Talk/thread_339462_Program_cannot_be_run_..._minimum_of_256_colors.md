---
title: "Program cannot be run ... minimum of 256 colors"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by SeaRox on 2007-01-15
I am running Ubuntu Edgy.  I installed wine and am trying to run a program but when it tries to start I get the following message:

"This program cannot be run with your current monitor settings.  Please reset your monitor to a minimum of 256 colors before running."

I looked in the menus and tried screen resolution but there is not option to change the number of colors.  I did a search in the forums and the wiki but found 0 results.  I may just be using the wrong search words.

It's probably simple but being new to Linux I haven't figured out how to change the number of colors the monitor uses.](*,) 

Any help?

---

### Post by carlosfocker on 2007-01-15
What graphics card do you have? Sounds like your drivers are not installed

Nvidia:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

Ati:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29)

---

### Post by SeaRox on 2007-01-15
Its an ATI.  I don't think its the driver though.  Everything else works.  It's just when I try to run this wine program.

Can I set the colors in wine?

---

### Post by carlosfocker on 2007-02-07
you can try:

```
wine explorer /desktop=Game,800x600 game.exe
```

What version of wine are you runnning? Just to check are you using fglrx drivers?

---

