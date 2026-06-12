---
title: "Problem with Fujitsu Siemens Amilo Li 1705"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Trixiante on 2007-10-18
Hello ! 
I've installed ubuntu 7.04, feisty fawn, on an Amilo li1705 laptop. Now, i think there are a few problems that i need to take care of before it could run as it's supposed to. When ubuntu starts it says " failed to allocate memory #6 to 10000@c0000 " or something like that. But it gets past it and loads the O.S. Just before the log-in screen pops there are some strange horizontal coloury lines(i reckon it has something to do with the onboard video card  - VIA Chrome9 HC DX9). Then ubuntu loads smoothly. Well, not too smooth because the only 2 screen resolutions available are 800x600 and 640x480. Also, when i try to ctrl+alt+shift+F1 for console, the same horizontal lines appear and the text is undecipherable. In Restricted Drivers "Atheros Hardware Access Layer(HAL)" is listed, enabled and in use. I tried to google my way out of this, but not having enough experience with linux i couldn't understand much of what was posted in forums. 
Can anyone explain what i have to do? (and i forgot to say, i don't have an internet connection on the laptop. Although i have one on the desktop and i can transfer stuff by an USB memory stick).
Thanks in advance! And if i haven't said things clear enough just say and i'll try to give more info.

---

### Post by mikeyphi on 2007-10-18
You might try this:

sudo dpkg-reconfigure xserver-xorg

enter the above command in a terminal - accept defaults but change the screen resolutions to ones you know work (careful!)

---

### Post by nsleiman on 2007-10-18
get the Gutsy 7.10 i think it will work out of the box.
i used to have probs with older versions (see my signature)

---

### Post by mikerobertso_UK on 2007-12-03
no 7.10 does not work out of the box with the li1705

---

