---
title: "No graphical thingy"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-04-25
Hi, i installed an Nvidia driver with envy today, but when i restarted it sayd that my graphical thingy (i didnt say thingy) was broken. So now i sit with the Live CD and want to reinstall the entire thing, but i dont want to loose the bookmarks and the user acounts, is there anny way of keeping them

Sry for my bad english but Live CD only works with US keybord, and i have NO  keybord so it\s har do write

---

### Post by udayan18 on 2007-04-25
wohhhhh...u dnt hv a keyboard..??..thn how do u write..?? i bet ubuntu doesnt hv voice recognition as in vista..!!

---

### Post by ajmannen on 2007-04-25
> **udayan18 said:**
> wohhhhh...u dnt hv a keyboard..??..thn how do u write..?? i bet ubuntu doesnt hv voice recognition as in vista..!!

Manny of the buttons don\t work, and those who work is in the wrong place. and the voice recognition in vista realy..........sucks. To be honest, i think all of vista suck

---

### Post by rocknrolf77 on 2007-04-25
> **udayan18 said:**
> wohhhhh...u dnt hv a keyboard..??..thn how do u write..?? i bet ubuntu doesnt hv voice recognition as in vista..!!


Keyboard layout NO (norwegian)

Login with your username and password at the command line

Try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```  

Pick the vesa driver. And then do a ```
sudo /etc/init.d/gdm restart
```] to start the x-server (the gui)
 
? is - and - is / on US layout

---

### Post by udayan18 on 2007-04-25
[http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)
:lolflag:

now u can get urself a keyboard.. now tht u hv saved quite a lot of money by installin a free OS  [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)

---

### Post by ajmannen on 2007-04-25
Newer mind the keybord, how can i reinstall or get back my graphical layout and ceep my bookmarks at the same time:confused:

> ubuntu@ubuntu:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070425181243
ubuntu@ubuntu:~$ sudo /etc/init.d/gdm restart
 * Stopping GNOME Display Manager...                                     [ OK ] 
 * Starting GNOME Display Manager...                                     [fail] 
ubuntu@ubuntu:~$ 





---

### Post by udayan18 on 2007-04-25
if u have all ur bookmarks in firefox installed on windows  thn u can import all those settings while u install ubuntu(i think step 5 or 6 of installation)

---

### Post by udayan18 on 2007-04-25
i think the same is possible wid ubuntu..(i had windows prior to installin ubuntu...n i imported all those settings in ubuntu)

---

### Post by slayerboy on 2007-04-25
What kind of graphics card do you have?  What version of Ubuntu are you using?

---

### Post by ajmannen on 2007-04-25
I have Ubuntu 7.04 and i don\t know what graphical card, but i think Nvidia.

And i don\t have windows

---

### Post by slayerboy on 2007-04-25
Ok so we've got an Nvidia graphics card and you tried using Envy to install the drivers?  Was this a fresh install of Fiesty or an upgrade from a previous version?

If this was an upgrade, try the solution I offer in this thread:
[http://ubuntuforums.org/showthread.php?t=422918](http://ubuntuforums.org/showthread.php?t=422918)

---

