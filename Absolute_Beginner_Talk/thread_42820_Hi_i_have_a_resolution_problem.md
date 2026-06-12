---
title: "Hi i have a resolution problem"
date: 2005-06-19
forum: Absolute Beginner Talk
---

### Post by dannyboyonline on 2005-06-19
Hi i succesfuly installed ubuntu but my resolution is no good.

How to set it up so that everything looks fine please?

I cannot see anything so real in detail directions would help, i managed to log in mtw but thats how far i got.

thanks

---

### Post by tread on 2005-06-19
You need to list some hardware details here, type of graphic card etc.
Also, search the forum once with your graphic card as a search string .. maybe someone has had a similar issue resolved.

Otherwise, come back here and someone should be able to help :)

---

### Post by estel on 2005-06-19
Alternatively, does [this](http://www.ubuntuforums.org/showthread.php?t=41787) help?

---

### Post by dannyboyonline on 2005-06-19
NVIDIA RIVA TNT2 Model 64/Model 64 Pro

This is my graphics card. 

I have no idea what resolution its running on and i'm not familiar with the OS to check.

It all looks like a lot of dots all different colours

The text it huge and most of it can be read with a little effort

---

### Post by TristanMike on 2005-06-19
To check - On the top bar...... System - Preferences - Screen Resolution, I think....  :) 

TristanMike

---

### Post by dannyboyonline on 2005-06-19
its 800x600

---

### Post by TristanMike on 2005-06-19
Should be able to change in that menu....I can.....just click on the little up and down arrows beside the current resolution....is that available for you?

---

### Post by Error_Msg on 2005-06-19
Open a terminaL and type this:
> sudo dpkg-reconfigure xserver-xorg
You're going to go into a BIOS Looking screen fuLL of settings, just navigate your way through it, and you wiLL find the resoLution settings there.

E_M

---

### Post by dannyboyonline on 2005-06-19
TristanMike yes but the screen is such a disgrace i can barely see thigs, i tried inproving the resolution from there it will only go down

---

### Post by dannyboyonline on 2005-06-19
I'm in the terminal dont have a clue what i'm writing though, is there a way where i can reboot the system into just the terminal like

restart in ms-dos mode in windows?

---

### Post by poofyhairguy on 2005-06-19
[QUOTE=dannyboyonline]I'm in the terminal dont have a clue what i'm writing though, is there a way where i can reboot the system into just the terminal like

restart in ms-dos mode in windows?[/QUOTE]

When the computer reboots, hit "esc" to see the grub menu. Pick the "recovery" option. Thats what safe mode in Linux is . :)

---

