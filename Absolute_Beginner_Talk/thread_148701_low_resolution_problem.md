---
title: "low resolution problem"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by mrli on 2006-03-22
Hello, I just installed Ubuntu on my pc(Using Matrox G450 Millenium video card). 
I'm stuck with 640x480 resolution only available in the System->Pref.-> Screen Rersolution dialog. After reading the posts here and checking /etc/X11/xorg.conf & /var/log/Xorg.0.log I don't see what is wrong.... Please help me.

---

### Post by mrli on 2006-03-22
Ok, managed to solve it through this guide :
[http://ubuntuforums.org/printthread.php?t=83973&pp=40](http://ubuntuforums.org/printthread.php?t=83973&pp=40)
though it was non trivial to find (alta-vista), while ubuntu-forums did not showed me this topic.
Thanks to everyone.

---

### Post by bfbay315 on 2006-03-22
Do you have the correct drivers for you card?

if so then... 

Find out what the refresh rate of your monitor is and set that in the monitor section of xorg.conf.

backup to be safe!!!!  
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old

TWO OPTIONS
------------------------------------------------
edit xorg.conf with vim or another text editor --
sudo vim /etc/X11/xorg.conf

OR  alternatively you can run 

dpkg -reconfigure xserver-xorg      #for you, I would recommend using this
You can pretty much blow through the config using dpkg.  
3 important things are 
- video driver selection
- pci address of card
- refresh rate of monitor




You'll need to restart the xserver to make your changes effective..

Brian

---

### Post by bfbay315 on 2006-03-22
nevermind

---

