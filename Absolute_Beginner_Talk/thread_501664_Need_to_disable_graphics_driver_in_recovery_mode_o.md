---
title: "Need to disable graphics driver in recovery mode or secure graphics mode"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by pointyblue on 2007-07-15
When I installed Ubuntu it chose a driver for my ATI accelerated graphics card that didnt quite fit the card. Graphics were slow and not as good as with the right driver.

Ubuntu had placed the correct driver under Restricted Drivers and I decided to try to enable it to see what would happen.

Shouldnt have done that! :(

Now the screen just turns black when Ubuntu starts. I can hear the startup jingle in the speakers so Ubuntu actually loads ok. Only the screen doesnt work.

I need a way to log in in secure graphics mode and disable the driver if thats possible or perhaps log in in recovery mode and disable the driver manually.

Any input on how to do this will be greatly appreciated!

---

### Post by testube_babies on 2007-07-15
Are you able to CTRL-ALT-F1 into a terminal?  If so, you can login and sudo nano /etc/X11/xorg.conf to change back to your old drivers.  If not, things get a lot harder :)

---

### Post by LLRNR on 2007-07-15
... Or it might be safer than to edit the /etc/X11/xorg.conf file to log in on one of the terminals (Ctrl+Alt+F1 ... Ctrl+Alt+F6) and run from there

```
sudo dpkg-reconfigure xserver-xorg
``` 

choosing the default answers and being careful just to change the driver for the graphics card.

---

### Post by avik on 2007-07-15
And if for some reason you can't access the command line, you can always edit the xorg.conf via a Live CD.

---

### Post by pointyblue on 2007-07-17
Thanks for all the ideas.

I switched to another screen of better quality. Ubuntu loaded as it should and everything worked ok. Disabled the graphics card driver, switched screens again and restarted Ubuntu - and everything works fine now.

---

