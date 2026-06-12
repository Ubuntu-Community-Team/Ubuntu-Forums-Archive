---
title: "ATI desktop effect problem"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by BloodThirstyEmu on 2008-02-04
When i try and click on normal and extra effects, it give me a window saying: The composite extension is not available. What do i do to fix it? I just installed the ati drivers for it, Could that be the problem?

---

### Post by chewit on 2008-02-04
What card are you using, i have a ATi 7000, works fine.

---

### Post by legend2440 on 2008-02-04
Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
Option "Composite" "1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl


Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

If the instructions above do not work or you just want to install the latest ATI drivers

I have ATI Radeon 9600 and I have found that the easiest way to install the newest drivers is with Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Envy not only installs drivers but will reconfigure the xorg.conf settings
It has always worked very well for me

---

