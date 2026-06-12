---
title: "unable to start 3D acceleration when trying to go OpenGL with a ATI RADEON X1650"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by stefaan.dutry on 2007-05-14
Graphics card: ATI RADEON X1650
ubuntu version: ubuntu 7.04 (fiesta fawn)
message: unable to start 3D acceleration

This problem happens when i try to run WoW in OpenGL using wine.
I doubt it's got something to do with wine or WoW.

I think it's got something to do with an uncorrectly installed graphics driver.
Or uncorrectly working.

I started by searching the forums.  I had no succes with what the steps explained in the ones i found :( 

I tried the installation instructions for the drivers on the ATI website.  Again no succes in solving the problem.

Is there a way to see if the drivers are correctly working?

Any help would be more than appreciated.

PS: if i've posted at the wrong spot, please direct me to the right spot then. :)

---

### Post by aeiah on 2007-05-14
perhaps this will help:

[http://ubuntuforums.org/showthread.php?t=438008&highlight=restricted+driver+ati](http://ubuntuforums.org/showthread.php?t=438008&highlight=restricted+driver+ati)

there is an option in feisty to install the restricted drivers for ati, and if this works for you, it may be the best solution. remember to back up your xorg.conf file before doing any changes in case it breaks ubuntu.

do use the restricted drivers in feisty go here:

[img]http://www.michaellarabel.com/external/restricted-0.jpg[/img]

[img]http://www.michaellarabel.com/external/restricted-1.jpg[/img]

---

### Post by aeiah on 2007-05-14
sorry i wasnt reading your post properly. i thought you meant you tried to install the ati drivers but got stuck or something, sorry.

you could test to see if opengl is running by running glgears or glxgears, for instance.

---

### Post by stefaan.dutry on 2007-05-14
Thx.
The problem is solved.

It was in the restricted drivers still and was not yet applied; therefore it could not go opengl.

Thank you for the fast response \\:D/

---

