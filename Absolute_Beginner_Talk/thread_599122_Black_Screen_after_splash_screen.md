---
title: "Black Screen after splash screen"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by SteveMallen on 2007-11-01
I had switched my auto login in the preferences and now I get a black screen with the circle with blinking lights spinning around. This seems similar to [http://ubuntuforums.org/showthread.php?t=484098](http://ubuntuforums.org/showthread.php?t=484098)), but I did not see a way to reverse my preference on the command side since I can't use the GUI. 

Thanks
Steve   ](*,)

---

### Post by Colro on 2007-11-01
After logging in (or when your screen is black and you SEEM to be logged in), press control + alt +F1, login, and type the command:

sudo nano /etc/gdm/gdm.conf

Look for the line that says "AutomaticLoginEnable=true" and change true to false. Then press control + X and then type Y to save your changes. After that, press control+alt+F7. If you're at a blank screen again and not at the graphical login screen after doing that, try doing control+alt+backspace.

---

### Post by SteveMallen on 2007-11-01
--------------------------------------------------------------------------------

After logging in (or when your screen is black and you SEEM to be logged in), press control + alt +F1, login, and type the command:

sudo nano /etc/gdm/gdm.conf

Look for the line that says "AutomaticLoginEnable=true" and change true to false. Then press control + X and then type Y to save your changes. After that, press control+alt+F7. If you're at a blank screen again and not at the graphical login screen after doing that, try doing control+alt+backspace.


Thanks for the quick reply....

Your instructions worked exactly as stated. When I got to the "AutomaticLoginEnable=" it was already false, so I switched it to true and saved. Restarted the computer and got right in. 

I added some little applet to try and have my keyring sinc so I would not have to log in to my wireless card every time I wanted to use the internet.

---

### Post by Colro on 2007-11-01
Glad it worked out :)

---

