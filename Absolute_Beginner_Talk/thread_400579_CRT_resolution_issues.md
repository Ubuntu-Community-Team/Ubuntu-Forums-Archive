---
title: "CRT resolution issues"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by mondoman89 on 2007-04-03
i am completely new to linux, so i dont know much. i successfully installed ubuntu on my old dell but everytime i get to the gnome desktop the resolution is all messed up. i tried lower the resolution in the system preferences menu but it resets and goes back to the login. i really need some help and im a total newb. its a D1226H dell monitor.

---

### Post by Scunizi on 2007-04-03
You're currently running a generic video driver which is ok.  What you'll need to do is reconfigure the driver to include the resolutions that you want.  There's a couple of things you'll need to do if the first doesn't fix it right off the bat.  First go to your terminal at Applications/Accessories/Terminal.  

This is like a DOS prompt if you remember that.  Now type (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak) and hit enter.  That just made a backup of your configuration file.  

Now type (sudo dpkg-reconfigure -phigh xserver-xorg) and hit enter.  It should ask you about which resolutions you want to configure for.  Only check off the ones that will actually work on your monitor.  

Once this is done give Ubuntu the three finger salute to restart the graphics (control - alt - backspace).  This is not like Windows... it's not a full reboot... just the graphics section of the computer.  Of course it will ask you to log in again.  

Now is the resolution fixed?  If not try to change it the way you did before, from the menus and let me know what happens.

---

### Post by eggybaby on 2007-04-04
This helped me out alot (though I didn't post the original) - Thanks.

---

### Post by oilchangeguy on 2007-04-04
what happens when you go to system, preferences, screen resolution? pick your res, click apply.

---

