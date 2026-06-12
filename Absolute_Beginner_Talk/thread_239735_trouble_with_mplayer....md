---
title: "trouble with mplayer..."
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Hranj on 2006-08-19
i cant get it to install. not only that but i dont even know where to start.

i tried using the add remove programs but that didnt install it. or at least 

cant find it if it did. im also having trouble navigating through my folders

and such. i can find eveything when i go to the places menu at top but not 

for example when im trying to find a place to download something. the folders

dont show. help?

---

### Post by taurus on 2006-08-19
Make sure you remove the # sign in front of all the lines with universe & multiverse in /etc/apt/sources.list.  Open a terminal (Applications -> Accessories -> Terminal) and type

```

gksudo gedit /etc/apt/sources.list

```
Save the chances and at the prompt, do

```

sudo aptitude update
sudo aptitude install mplayer

```

---

### Post by GeekSpeek'r on 2006-08-19
had a problem too with "mplayer" --> try kmplayer

sudo apt-get install kmplayer

should work dandy.

---

### Post by eXcentra on 2006-08-19
Get "gmplayer" if you're on gnome. :p

---

### Post by Hranj on 2006-08-19
ok so i took GeekSpeek'r's advice but now how do i get MP3 support as well as other movie and music codecs?

---

### Post by Big_J on 2006-08-19
For mp3, get XMMS, it's like winamp and works really well.
For videos, I suggest using VLC Media Player, it plays almost everything for me.

---

### Post by GeekSpeek'r on 2006-08-19
so, yes. But for the newly inducted...

sudo apt-get install xmms

its all good...........

---

### Post by Hranj on 2006-08-19
thanks a bunch you guys.

---

