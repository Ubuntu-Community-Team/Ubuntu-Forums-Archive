---
title: "aMule to Amarok"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by LinuxLoserr on 2007-08-20
I have both amarok and amule, however i would like to put my music from aMule to amarok.
I don't know which file contains music from amule or amarok, does anyone know them?
As well, how do i make it able to play music from amule, because it doesnt let me play them..

---

### Post by Acglaphotis on 2007-08-20
Just copy the songs (they are in /home/user/.aMule/Incoming/) to your normal music folder and amarok will find them instantly.

---

### Post by LinuxLoserr on 2007-08-20
For some reason, i don't have a .amule file there..

---

### Post by Acglaphotis on 2007-08-20
Try pressing Control+H. (while you are in nautilus)

---

### Post by LinuxLoserr on 2007-08-20
yeah you were right, thanks.

---

### Post by LinuxLoserr on 2007-08-20
woah, now apparently amarok has no mp3 support?

---

### Post by StooJ on 2007-08-20
Ubuntu does not include codecs for proprietary formats (such as mp3s) out of the box, since they are not "Open source".

It's very easy to get them, however. This might be what you're looking for:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

---

### Post by Acglaphotis on 2007-08-20
Do they play in Totem?

---

### Post by LinuxLoserr on 2007-08-21
yes they do, they play in totem, however i would like to have playlists and such.
trying the codec thing now.

---

### Post by Hallvor on 2007-08-21
If a Winamp clone will do, there is XMMS which uses its own codecs. You don`t have to install other codecs to make it work. The same with VLC media player for video content. There is really no need to install codecs at all, if you are happy with XMMS and VLC.

```
sudo apt-get install xmms xmms-skins xmms-wma

```

---

### Post by LinuxLoserr on 2007-08-21
Alright i downloaded xmms and it worked all right.
thanks for all the help guys.
and now i know not to trust a guy by the name of mettais ettrech :)

---

