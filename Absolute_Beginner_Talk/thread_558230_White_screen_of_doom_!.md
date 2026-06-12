---
title: "White screen of doom !"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by ThRixXx on 2007-09-23
I changed some setings on my computer, including removing "Envy"...

Now i tried google, i lloked at any way i could find to fix this ! Now im gona ask u guys for help :D

When i put my PC it says ubuntu and it loads... Then my loging screen comes.. I type in my username and then my password.  Then the llightbrownish retangle thing comes up in the middle.  After a while that rectangle turns white and EVERYTHING ELSE black.  After a few seconds everything just turns white ! 

Sorry but im really noob !

---

### Post by Pumalite on 2007-09-23
Ctrl+Alt+F1 to get a command line.
sudo dpkg-reconfigure xserver-xorg. choose most defaults, choose 'vesa' as the driver, then: startx
Hope it helps.

---

### Post by overdrank on 2007-09-23
> **ThRixXx said:**
> I changed some setings on my computer, including removing "Envy"...

Now i tried google, i lloked at any way i could find to fix this ! Now im gona ask u guys for help :D

When i put my PC it says ubuntu and it loads... Then my loging screen comes.. I type in my username and then my password.  Then the llightbrownish retangle thing comes up in the middle.  After a while that rectangle turns white and EVERYTHING ELSE black.  After a few seconds everything just turns white ! 

Sorry but im really noob !

Hi if you removed envy then you remove your drivers, you can reconfigure your xorg. Use the alt,ctrl,F1 keys all at the same time and this will bring you to the terminal and login. Then use the command ```
sudo dpkg-reconfigure -phigh xserver-xorg 
``` answer a few questions and then reboot
```
sudo shutdown -r now
``` Hopefully this will bring you back to the desktop. Good luck!

Edit to slow

---

### Post by ThRixXx on 2007-09-24
NOPE, its still not working ... What else can i do ?

---

### Post by alienexplorers on 2007-09-24
Does anything show up on your screen or is it totally white?  What graphic card are you using.  What drivers do you have loaded?

---

### Post by ThRixXx on 2007-09-24
Nope, i explaned what happens.. Its all white !! I have a GeForce 5900 and i was running Envy but i removed it

---

### Post by alienexplorers on 2007-09-24
May I sugest you rerun envy.  Remember to remove old drivers before installing new ones.  Once installed you should have access to nvidia-settings to configure your card.  Envy homepage is listed in my sig line below.

---

### Post by ThRixXx on 2007-09-24
how do i rerin envy if i cant go onto my computeR ?

---

### Post by ThRixXx on 2007-09-24
help please, before this topic moves to the 342524page...

---

### Post by ThRixXx on 2007-09-24
..... help.....

---

### Post by alienexplorers on 2007-09-24
When you get the white screen go and enter ctrl-alt-F1.  You should enter a terminal there.  Login with your name and password.  Run from the prompt:
> sudo dpkg-reconfigure xserver-xorg
If asked to select a driver, go with nv for now.  Answer the rest of the questions.
reboot and see what happens.

---

### Post by ThRixXx on 2007-09-24
tried that 20 times, its stil just white !!!

---

### Post by alienexplorers on 2007-09-24
You mentioned running envy.  That means you downloaded it and installed it.  Well from the ctrl-alt-F1 prompt you should be able to run envy.
Run:
> sudo envy -t

If that does not take care of the problem I don't know what will.

---

### Post by alienexplorers on 2007-09-24
You mentioned a brown rectangle.  That loaads metacity, nautilus, and gnome-panels.  I wonder if you lost these things.  You could try to reinstall them from the command prompt you get with ctrl-alt-F1
> sudo aptitude install metacity 
sudo aptitude install nautilus 
sudo aptitude install gnome-panels

---

### Post by ThRixXx on 2007-09-24
Wow Yay Fanx That Envy Thing Worked Like A Bomb !@@@@@@@@@@@@@@@@@@@@@@@$!$!$!$!$!$

---

