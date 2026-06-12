---
title: "How do you make X Windows register my dual display as two seperate monitors?"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by Sootah on 2008-04-21
I have dual displays working in X courtesy of using Envy and nVidia's X Server Settings manager.

The desktop itself along with all the apps work fine. It's with apps that want to go fullscreen that are the issue (games under Wine)

Currently all the games detect my display as 3360x1050, which is true as far as my desktop space is concerned, but obviously double what I can display on one monitor. X Windows itself registers my displays as one huge device, so I'm curious if there's a way to make X register the displays as seperate entities.

Alternatively, perhaps if we simply add 1680x1050 as a display mode in the X conf file then the games will let me select that resolution. (The *only* res available as a selection is 3360x1050)

Below is a screenshot of how X sees the displays, as well as how nVidia's X configurator sees them.

[IMG]http://tweaksforgeeks.com/images/X_Res.jpg[/IMG]

[IMG]http://tweaksforgeeks.com/images/nVidia_X.jpg[/IMG]

Linux is still very foreign to me, but I'm slowly grasping how things function. I like to not only understand how to get things done, but also I have a need to know how they work on the back-end. Any recommended reading for that?

---

### Post by Confuzius on 2008-04-21
Stick with twinview and add metamodes your xorg.conf file.
Check here: [http://ubuntuforums.org/showthread.php?t=416249](http://ubuntuforums.org/showthread.php?t=416249)

I have mine set up as (1680x1050, null) when I enter a full screen game the second monitor turns off, not the best option, but it seems to work alright for me.

---

### Post by forestpixie on 2008-04-21
Try to configure as seperate X screens on the nvidia-settings display tab

---

### Post by Confuzius on 2008-04-21
If I remember correctly you can not drag things from one X screen to the other, which makes setting up two different ones more of a pain in the butt.

---

