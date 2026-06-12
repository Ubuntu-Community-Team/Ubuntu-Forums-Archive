---
title: "installing nvidia-glx crashes me on reboot"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by lumarh on 2007-03-12
When i install the nvidia-glx drivers and reboot as instructed, the graphics server (is it xorg) just crashes and gives me a big text wall talking about how it didnt work...(same thing for legacy drivers but im not supposed to use them anyway)

I think it might have something to do with it putting the comp in a refresh rate that isnt supported... a friend once got the drivers working for me but that was a long time ago.

i have a geforce 5700, LG flatron L1717S.

I think its a matter of changing/adding some values in xorg.conf.... could somebody please help? thanks

---

### Post by Kobalt on 2007-03-12
Did you run ```
sudo nvidia-xconfig
``` after you installed the drivers ?

---

### Post by lumarh on 2007-03-12
no i didnt, is there anything in particular i should do in the config

---

### Post by NikoC on 2007-03-12
Try running the command Kobalt suggested, it should do the trick in configuring your nvidia driver.
In case it doesn't and xorg gives you errors you can always do:
sudo nano /etc/X11/xorg.conf
find the 'device section'
and replace "driver" "nvidia" by "driver" "nv"
save the file
sudo /etc/init.d/gdm restart

At least you are able to use your GUI (gnome, KDE, XFCE,...) again that way

---

### Post by lumarh on 2007-03-12
the first sudo command worked...

wow , so simple after so much buggering around. you'd think this command would be mentioned in the ubuntu help guide. 
 thanks much for the help guys


edit: follow up Question, now that the driver is working i seem to have lost the option of a resolution, whatever the next one up from 1024-768 is, i think its 1200 x somehitng or thereabouts.... how do i get it back

edit2: nevermind fixed it myself damn i love linux thakns yall

---

