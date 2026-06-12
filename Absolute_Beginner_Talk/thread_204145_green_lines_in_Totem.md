---
title: "green lines in Totem"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by bullon on 2006-06-26
when i play video in totem it sometimes renders green lines and distorts the image. Here's a screenshot so that you can better unserstand what i talkng about:

[IMG]http://www.freewebtown.com/tiox/Screenshot.png[/IMG]

i using totem-xine.

---

### Post by Anduu on 2006-06-26
I have come to the conclusion that Totem is far from the best choice in media players...try mplayer or vlc...my player of choice is mplayer.

---

### Post by catlett on 2006-06-26
I prefer xine. It is sleek and runs great for me.
```
sudo apt-get install xine-ui
```
If you want to associate xine-ui to play multimedia files 
```
gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "xine dvd://" 
sudo rm -f /usr/share/applnk/Multimedia/xine.desktop
sudo ln -fs /usr/share/xine/desktop/xine.desktop /usr/share/applications/
sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sudo sed -e 's/totem.desktop/xine.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
sudo mv /tmp/defaults.list /usr/share/applications/defaults.list
```
Just in case you are interested.

But also what type of video card do you have?

---

### Post by bullon on 2006-06-27
i installed vlc, its what i used to use in windows, great app. The grren lines are still there but only when i use xvideo as my output module, searching for a fix right now... thanks for the help!

---

### Post by nevin on 2006-07-06
hey, if you find a fix, post it, cause i have the same problem!  and it sucks

---

### Post by Bickyrib on 2007-03-29
Problem is easy to solve.
In Totem. Put On the deinterface "I" Key or just search it in the top menu's.

In VLC I put my output mode in X11 and it also works
You can select this at video --> export modules
don't forget to activate "advanced options"

---

