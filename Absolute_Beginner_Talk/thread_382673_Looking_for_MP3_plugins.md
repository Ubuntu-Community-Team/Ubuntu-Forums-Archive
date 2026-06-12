---
title: "Looking for MP3 plugins"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-03-12
I'm looking for MP3 plugins for my audio players. I've gone to this link

[https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59](https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59)

which is part of my frustration with Linux -- the instructions are often good, but something has been changed in the software since the instructions were written (actually fairly recently) which renders them useless. There's no where to click "Add."

I looked under the Third Party tab which asks for the address of an APT repository (and which contains an Add button). What in the world is an APT repository?--and how do I get to it?

I'm still looking for MP3 plugins.

---

### Post by Bachstelze on 2007-03-12
Please hold on a sec. while I ask my crystal ball what version of Ubuntu you run so I can give you more detailed insructions ;)

---

### Post by lwalper on 2007-03-12
Thanks for your persistance!!

ver 6.10

---

### Post by Bachstelze on 2007-03-12
And what are the apps you want mp3 support in - please give names, not "all of them" ;)

---

### Post by lwalper on 2007-03-12
Rhythmbox, Totem, and any other *common* player.

Also, I've installed Lame 3.97 which enabled the write to MP3 function in Audacity. In the WinOS there was a Lame interface -- is that available in this that I just installed to Linux?

---

### Post by Bachstelze on 2007-03-12
Well, actually, the player is two things : the frontend and the backend. Totem and Rythmbox are frontends, meaning that they do the job of displaying the gui and the buttons and let the backend do the job of actual playback. Common backends are Xine and Gstreamer. I don't know what backend Rythmbox uses the Gstreamer backend so to install mp3 support, you do :

```
sudo apt-get install gstreamer0.10-plugins-ugly
```

Totem can use either Xine or Gstreamer as it's backend. I don't remember wich version of it (totem-xine or totem-gstreamer) Ubuntu installs by default, you can find it with :

```
dpkg -l | grep totem
```

---

### Post by lwalper on 2007-03-12
WOW!!! Thanks. Works like a charm. I *really* appreciate your patience --- and promptness!

---

