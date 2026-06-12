---
title: "music player"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by tim1970 on 2007-02-16
What is a good music player?  I am currently using rhythmbox, but it looks like an eyesore, even with the small view.  What is a good music player, that will look good on the desktop, while it is playing.

THanks

---

### Post by dbbolton on 2007-02-16
lauri taimila made some icon improvements for rhythmbox. 

**wget** [http://taimila.com/downloads/rhythmbox_extra_icons.tar.gz](http://taimila.com/downloads/rhythmbox_extra_icons.tar.gz) 

and extract the archive. then 

**cd **to the folder containing the extracted files.

```

#     sudo mv stock_shuffle.png /usr/share/icons/Human/24x24/actions/

#     sudo mv stock_music-library.png /usr/share/icons/Human/24x24/actions/

#      sudo mv stock_repeat.png /usr/share/icons/Human/24x24/actions/

#      cd /usr/share/icons/

#      sudo gtk-update-icon-cache --force Human

#     sudo ln -s /usr/share/icons/Human/scalable/devices/gnome-dev-cdrom-audio.svg /usr/share/icons/Human/scalable/apps/gnome-media-player.svg

#      sudo gtk-update-icon-cache --force Human
```

in my opinion, no other music player beats the simplicity of rhythmbox. you might try Listen, Quod Libet, or Amarok if you want something flashier. Beep media player integrates well with the ubuntu desktop, imo.

---

### Post by esaym on 2007-02-17
some options:

[http://ubuntuforums.org/showthread.php?t=335189](http://ubuntuforums.org/showthread.php?t=335189)

---

### Post by r4ik on 2007-02-17
Amarok.

---

### Post by soham on 2007-02-17
Songbird ftW

---

### Post by ricardisimo on 2007-02-17
They have yet to improve upon XMMS, but its days are clearly numbered, unfortunately.

---

### Post by Spr0k3t on 2007-02-17
> **soham said:**
> Songbird ftW

Even in alpha state, I'm loving songbird.  To go with songbird, grab Ex Falso for ID3 tag editing.

---

### Post by ricardisimo on 2007-02-17
Better than EasyTag? ET is a bit quirky, so if anyone has tried both and can recommend one or the other, I'll go with that.

---

### Post by 3rdalbum on 2007-02-17
If you've already got Ex Falso for tag editing, you might as well install Quod Libet (music player) - it's only an extra couple of kilobytes, and it's worth a look.

---

