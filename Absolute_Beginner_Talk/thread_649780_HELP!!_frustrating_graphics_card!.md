---
title: "HELP!! frustrating graphics card!"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by 900donuts on 2007-12-25
heres the situation
 i got a new graphics card this morning (YAY:)!) it a evga e-geforce 6200LE
 but its not working (WAH:(!)
i disabled the old drivers switch the cards booted up (low res) downloaded the drivers form the restricted drivers manager rebooted and got an error message saying that it could not detect the graphics card and monitor correctly reverting to the generic monitor and vesa card setting i tweaked for a while trying to get it to work but every time i tried to load the up to date drivers i would be back at square one i then tried another card i had lying around that worked back in a 7.04 (its a nvidia geforce fx 5200) and the monitor lost the signal  when it tried to display the login screen so i'm back at my 4400ti i restored most of the graphics capabilities accept the 3d desktop which lost the ability to make borders and title bars

what should i do?

---

### Post by SOULRiDER on 2007-12-25
Connect the **new** card and then reconfigure hte X server. Follow these steps on a terminal.

1- Backup your config
```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

2- Reconfigure the X server
```
sudo dpkg-reconfigure xserver-xorg
```

Please post your results.

---

### Post by 900donuts on 2007-12-25
what will the bottom code do?

---

### Post by TidusBlade on 2007-12-25
According to the thing, it will probably reconfigure Xerser-xorg accordingly to your system?

---

### Post by SOULRiDER on 2007-12-25
Its a wizard to help you configure xorg so that it works.

---

### Post by Pabx on 2007-12-25
You have to download the driver from nvidia's webpage, then put it in your desktop... then press ctrl+alt+f1, and it will take you to terminal. Then log in and type ```
cd Desktop
``` and then ```
sudo /etc/init.d/gdm stop
``` and the last is typing ```
sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run
``` Follow the steps and Reboot....

---

### Post by SOULRiDER on 2007-12-25
Installing the drivers you download fromt he site isnt a good idea. Not only they are harder to install but they wont auto-update and there may be some problems with the kernel-headers that are needed for them to work. The best thing is to have a working xorg and then install the drivers witht he restricted manager or by using envy.

Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by 900donuts on 2007-12-25
the xconfig thing seems to have fixed it (THANKS!:)) i can do thing like enabling the 3d desktop but when i enable the effects the title bars still disappear how do i fix that?

---

### Post by Steveway on 2007-12-25
You need to run a Window-manager.
Install and run Emerald, that should fix it.

---

### Post by 900donuts on 2007-12-25
i had already installed emerald but no themes to choose from are coming up

---

### Post by SOULRiDER on 2007-12-25
Only install/use emerald if you want, its not needed and i personally dont like it.

To fix decorations (thats hte name of the title bar) use this command
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24 
```

I took it fromt he troubleshooting section here:
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)
you might wanna take a short look at it.

---

