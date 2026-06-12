---
title: "Can't install drivers"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by danbrownlow on 2007-11-22
Hey all, I have got all the drivers I need, but I have a weird and annoying problem, When I run the executable, it runs, but I can't see the buttons at the bottom, so I can't click them.. which means I can't install the drivers.. I can't seem to resize the screen either, Anyone know how to solve this?
Dan

---

### Post by taurus on 2007-11-22
What driver are you talking about?  Is it for your graphic card?  Are you running at a low resolution?

You can reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When done, press <Ctrl><Alt>Backspace to restart X again.

---

### Post by danbrownlow on 2007-11-22
Yea', I'm installing drivers for the ATI Radeon 2600XT and I got them off the ATI site. When I open and run the program, it asks whether I want to install, but because of the rubbish screen resolution I can't get down the bottom lol. I tried the command above but no look, it didn't seem to change anything after I restarted X again.

---

### Post by danbrownlow on 2007-11-22
No worries we fixed it.. We delete all the other options avaible and it seemed to work LMAO! Hwo good is that.

---

