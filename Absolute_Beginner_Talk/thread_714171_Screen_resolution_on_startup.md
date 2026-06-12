---
title: "Screen resolution on startup"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by rhoward on 2008-03-03
I have a flat panel, wide screen dell monitor. I also have Nvidia Gforce 5200 Graphics card. So ,here is my problem:  when I try to instal Ubuntu, the display I have is 800x600, much to large for my screen. I cannot change the resolution to fit my screen. The forward button is way below range and my mouse will not pick it up either. Sometimes, I've found that just hitting enter will take you to the next screen when installing,, but not so here. I get the message" Are you sure you want to quit? I have no choice but to quit and i cannot install Ubuntu. Does someone have a solution to this problem?
Thanks
Bhoward

---

### Post by wolfen69 on 2008-03-03
this is for installing ubuntu on a eeepc, but may work for you:

"It should be noted that due to the small display and lower resolution the Ubuntu installer does not fit within the confines of the screen. You'll need to use your ALT key in combination with dragging the mouse to move the active windows around in order to find the "Next" buttons." [https://help.ubuntu.com/community/EeePC](https://help.ubuntu.com/community/EeePC)

then, once you get to your desktop, do in terminal:

**sudo dpkg-reconfigure -phigh xserver-xorg**

you can then set your desired resolution. then do ctrl-alt-backspace to reset x.

---

### Post by dstew on 2008-03-03
You can pull up the window with Alt-mouseclick.

---

### Post by owbizi on 2008-03-03
Or using tab (the key above caps lock) to get to the option you want to choose, with space or enter.

---

