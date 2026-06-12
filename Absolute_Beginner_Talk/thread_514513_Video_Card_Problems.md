---
title: "Video Card Problems"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by penofallpens on 2007-07-31
I just installed Ubuntu Studio onto my computer and am trying to learn Linux.  However, after I pass the loading screen, before login, my monitor simply stops showing anything.  I have a Nvidia Geforce 5200 card.  I borrowed a Geforce 4 MX 440 from a friend and I can run Ubuntu with this card.  What can I do to get my video card to work?

---

### Post by nitro_n2o on 2007-07-31
log into a terminal (by pressing Alt+F2) while booting (splash screen) try to get your basic screen functionality by typing ```
sudo dpkg-reconfigure xserver-xorg
``` it'll ask you some questions and should give you the basic functionality. 
When you get it, or if you didn't get it at all, try installing the nvidia drivers from the terminal 
```
sudo apt-get install nvidia-glx 
```and restartX or restart the machine once you get your screen you can also install nvidia-settings 
```
sudo apt-get install nvidia-settings 
``` which is a nice tool to graphically edit your settings run it by typing 
```
gksudo nvidia-settings
``` and play as u wish. 
have a search in the forums it's full of nvidia and graphics setups 
have fun

---

