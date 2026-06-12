---
title: "Make Xine the default player"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by TheAnonymousx on 2005-11-17
Hey guys, I'm wondeirng how to make Xine my default DVD player (it's installed and working, just wondering how to make it the default).

---

### Post by rado_london on 2005-11-17
```
gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "xine dvd://"
sudo rm -f /usr/share/applnk/Multimedia/xine.desktop
sudo ln -fs /usr/share/xine/desktop/xine.desktop /usr/share/applications/
sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sudo sed -e 's/totem.desktop/xine.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
sudo mv /tmp/defaults.list /usr/share/applications/defaults.list
```

---

### Post by TheAnonymousx on 2005-11-22
Heh it appears mplayer still wants to be the defualt player for my DVDs. I'll poke around with this more unless someone has some more suggestions.

---

