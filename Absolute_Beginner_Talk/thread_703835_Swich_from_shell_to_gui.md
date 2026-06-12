---
title: "Swich from shell to gui"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Dragoola on 2008-02-21
Hi, I was trying to install Ubuntu on my pc and I got stuck at one point. I didn't burn a CD as none of my burning programs work at this moment. However I found some sort of windows installer and I think it worked. However when I boot my computer into ubuntu it doesn't end up in the GUI but in something that I believe is the shell and I can enter commands there. What should I do to get to the GUI, is there a specific command or do I have to burn a cd and do everything from the beginning?

---

### Post by taurus on 2008-02-21
Did you install the server version?  If you did, then you need to install a desktop so you would have GUI.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by overdrank on 2008-02-21
> **Dragoola said:**
> Hi, I was trying to install Ubuntu on my pc and I got stuck at one point. I didn't burn a CD as none of my burning programs work at this moment. However I found some sort of windows installer and I think it worked. However when I boot my computer into ubuntu it doesn't end up in the GUI but in something that I believe is the shell and I can enter commands there. What should I do to get to the GUI, is there a specific command or do I have to burn a cd and do everything from the beginning?

HI and welcome, was the installer WUBI? You can try the command startx. What is the graphics card on the system?

---

### Post by Doorslammer on 2008-02-21
try ```
 start x 
```
or if you have to install the desktop
```
sudo apt-get update
```
```
sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
you may need this to
sudo dpkg-reconfigure xserver-xorg
```
edit
you guy's are fast by the time I made my post you guy's had posted what I was going to post .

---

### Post by Dragoola on 2008-02-21
Hi, you guys are so fast :). Yes, the command was WUBI. I tried using startx but it did not work. My video card is a Radeon x1650. There is another thing that might be causing the problem, I downloaded the version for 64 bit processors and the name of the image has some amd in it. My processor is intel core duo E6300 and now I think it might not be 64 bit. Anyways, now I'll try updating as you guys told me and see if I can work it out.

---

