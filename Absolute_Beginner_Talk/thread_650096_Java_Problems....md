---
title: "Java Problems..."
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Ubun2User on 2007-12-25
Okay so this is my wife's computer and it has Ubuntu on it.  Everything has been working fine and now she tried to log onto MySpace and it said that it needed to install missing plug-ins for Java.  Flash player was already installed so we installed the other choice.  I also went to Apps > Add/Remove Programs and added Java in there.

Now it no longer says that Java or Flash needs to be installed but all movies and music has stopped working...please help!

---

### Post by taurus on 2007-12-25
Try installing ubuntu-restricted-extras again.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Ubun2User on 2007-12-25
Still not working.

---

### Post by taurus on 2007-12-25
Can you be a little more specific?  MP3 won't play, vlc won't play movies, etc.?

---

### Post by Ubun2User on 2007-12-25
It won't play music on MySpace and it won't play slide shows specifically.

---

### Post by LaRoza on 2007-12-25
MySpace is usually loaded with invalid scripts and multimedia.

It is no wonder it doesn't work in standards compliant browsers on Linux.

---

