---
title: "tried to install the intel driver for my video chips"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by tony404 on 2007-06-23
I have a gateway laptop tried to install 915 resolution so I could up my resolution.Installed it rebooted and all I got was scrambled graphics. So I tried dkpg-reconfigure xserve-xorg, now it boots I go past the login and then I get  a white screen with a cursor I can move around nothing else. Any thoughts how to fix :)

---

### Post by gn2 on 2007-06-24
Perhaps try "sudo dpkg-reconfigure -phigh xserver-xorg" and select a different driver to the one you have now.

---

### Post by tony404 on 2007-06-25
it didnt work any other ideas :)

---

### Post by ramjet_1953 on 2007-06-25
What is the native resolution of your screen?

You may want to have a look at this:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

As you will see, there are two alternatives. The easiest is to install xserver-xorg-video-intel, but for some systems it doesn't work, especially if you want to run games that use full-screen and that change the scrren resolution dynamically.

Still the best is 915resolution, but you may have to configure it. It is still much easier than fiddling with your xserver.xorg.conf file.

Regards,
Roger :cool:

---

