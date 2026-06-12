---
title: "Geforce 8600gt graphics card, but only 50/51hz refresh rate!"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Bellicus on 2008-04-01
The title says it all. I can't get my refresh rate higher then 51 and its on 50 by default, feels like glaring at screen is going to smelt my face and make my eyes pop out.

Ubuntu 7.10 found a driver for geforce 8series and is using it. On windows i have 75hz and higher in some games. The resolution is 1280x1024, so its strange that the refresh rate should be so low.

I installed ubuntu yesterday, so if you got time and knowledge, please make it simple :)

---

### Post by overdrank on 2008-04-01
> **Bellicus said:**
> The title says it all. I can't get my refresh rate higher then 51 and its on 50 by default, feels like glaring at screen is going to smelt my face and make my eyes pop out.

Ubuntu 7.10 found a driver for geforce 8series and is using it. On windows i have 75hz and higher in some games. The resolution is 1280x1024, so its strange that the refresh rate should be so low.

I installed ubuntu yesterday, so if you got time and knowledge, please make it simple :)

Hi and did you install the restricted drivers located under system, administration? If yes then you can use the nvidia settings by using the alt,F2 key and enter the command ```
gksudo nvidia-settings
``` and change your refresh rate there.
If not you may look at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Bellicus on 2008-04-01
Jay! Thanks alot :) Feels MUCH better now.

But a final question, is there a way to put the controll panel for nvidia on the desktop or anywhere else, or do i have to remember this command?

---

### Post by 3rdalbum on 2008-04-01
You can create a launcher for that command, or add it to the Applications menu. For instance, right-click on the Desktop and choose "Create Launcher". Under the section "command", put in that command. Or, if you right click on "Applications" on the top-left corner of the screen, and then go Edit Menu, you will be able to add that command to your menu.

---

### Post by CJ56 on 2008-04-01
nvidia-settings should be lurking in usr/bin (or at least it is in mine). You can attach a launcher to it & if you hunt around for an icon - try usr/share - you should be able to find an Nvidia icon & attach it to the launcher and put it wherever you want. 

I've currently got mine sitting on my AWN dock & it is pretty useful... ;)

---

