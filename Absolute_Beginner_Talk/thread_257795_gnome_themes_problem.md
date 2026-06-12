---
title: "gnome themes problem"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-09-15
I have been having problems with gnome since installing some themes recently.  Now whenever I try to change to ANY theme, even the ones that come with Ubuntu, I get messages saying that the clock has stopped working and various other things too.  Then when I reboot gnome wont start properly. After login I just get a brown screen with the bars at the top and bottom flashing.  I have found from another thread I started, how to rectify this, but how can I get rid of all the themes that I have installed so that I can at least change to some of the other Ubuntu installed themes?  Is there any way of reinstalling gnome completely?  I have KDE installed so I can switch to that to make any changes to gnome if that helps.

Russty.

---

### Post by petri on 2006-09-15
I don't know about uninstalling the themes but your can [uninstall]("http://www.psychocats.net/ubuntu/purekde") and [reinstall]("http://www.psychocats.net/ubuntu/gnome") ubuntu-desktop with aysius guide.

If your first install was Ubuntu then i don't know what happens to your start splash...

---

### Post by Russty of Oz on 2006-09-15
Thanks for that.  I had a read, and I did the remove with aptitude, but it didn't remove gnome.  I installed Ubuntu and then added KDE, so it looks like the rest of that page may not work for me, as it is to remove gnome from Kubuntu, I think.  

I have made enough mistakes lately so don't want to try anything that might screw it all up again.  

Russty.

---

### Post by petri on 2006-09-15
No you can't remove it with aptitude because it isn't installed with aptitude. You have to include everything that comes after apt-get 
```
sudo apt-get remove alacarte app-install-data-commercial at-spi avahi-daemon bittorrent and so on...
```
just copy and paste it in terminal.

When you install gnome again then you will use ```
sudo aptitude intall ubuntu-desktop
``` but do it as it is written on his website.

---

### Post by Russty of Oz on 2006-09-15
Ah!  Thanks I will try that.

Russty.

---

