---
title: "make vlc default player... for real (KDE)"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Xiong Chiamiov on 2008-01-13
(I'm using KDE)
So, I have some nice .ogm files that I'd like to watch in vlc.  When I right-click -> properties -> wrench-thingy, vlc's at the top of the list.  Also, I've done an open-with and checked the "always use this"; vlc played it just fine, but kaffeine is still the default for all my .ogm's.  Kaffeine's ok, but I prefer vlc, and I'd prefer to reduce my number of clicks.  Any thoughts?

---

### Post by nikoPSK on 2008-01-13
Open kcontrol, and navigate to the File Associations setting. I don't use KDE much but I can take you that far :)

---

### Post by Xiong Chiamiov on 2008-01-15
> **nikoPSK said:**
> Open kcontrol, and navigate to the File Associations setting. I don't use KDE much but I can take you that far :)
I looked around in the control panel before, but all I can find is the "Default Applications", which is only for web, email, im.

I uninstalled kaffeine before, but it made amarok not work (something to do with xine? idk), and, well, overall, I'd like to have 'em both.

---

### Post by RomeReactor on 2008-01-15
Hi. One of Kaffeine's backends depends on the Xine libraries (this is the default; the other one being dependent on Gstreamer), as does Amarok; when uninstalling Kaffeine make sure to only remove the program and not its associated libraries:
```
sudo apt-get remove kaffeine-xine
```
And:
```
sudo apt-get install libxine1 libxine1-ffmpeg libxine1-plugins xine-plugin amarok-xine
```
To make VLC the default player for OGM files, right click on an OGM, select "Properties", and mark the VLC radio button (it doesn't mater which one is at the top; what matters is the selected player).

---

### Post by nikoPSK on 2008-01-15
> **Xiong Chiamiov said:**
> I looked around in the control panel before, but all I can find is the "Default Applications", which is only for web, email, im.
 
I uninstalled kaffeine before, but it made amarok not work (something to do with xine? idk), and, well, overall, I'd like to have 'em both.
 
Sorry, only basic KDE knowledge... :(, will learn more as time passes by.
 
nikoPSK

---

