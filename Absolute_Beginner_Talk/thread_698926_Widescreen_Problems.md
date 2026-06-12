---
title: "Widescreen Problems"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by darthlunchbox42 on 2008-02-16
I purchased a new 22" Acer AL2216W monitor today.  After plugging it in I booted to Ubuntu and it worked like a charm, I had widescreen in all it's glory.  But then I restarted and booted into Windows to play a game, and when I came back to Ubuntu the login screen was fine, but after that it wasn't widescreen and I couldn't make it go above 1400x1050.  When I try and change things about in Screen and Graphics Preferences, it doesn't accept anything I do.  I click 'OK' and nothing happens.  Some how I got the 'Model' selection to be Acer AL1916W (widescreen) from Plug - and - Play.  Despite saying widescreen and having a different model selected, there has been no change to my resolution.  I don't recall what I had it set to previously, but I know that it was widescreen and a much 'larger' resolution than what I'm stuck with now.  

Just an FYI, I am *completely* at a loss of any and all commands that one puts in the terminal, so be prepared for a thousand questions to come your way.  :)

---

### Post by smartboyathome on 2008-02-16
First, what graphics card do you have? It could be the source of the problem if you had a kernel update, as the kernel update might have wiped the driver. Also, consider trying this if you didn't use a 3rd party tool to install the graphics driver or if you don't have an NVidia card (if you have one, this can mess up your computer, instead run nvidia-settings):
```
sudo cp xorg.conf xorg.conf.bkup
sudo dpkg-reconfigure xserver-xorg
```
This will backup your xorg.conf (the file which holds all your graphical configurations) and take you through a text-install to reconfigure your graphics. Select the resolutions and the card you would like to use.

---

