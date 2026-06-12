---
title: "Save dvd to drive then play"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-07-20
I want to save a couple of my DVDs to my computer then play them back.  I right clicked on the DVD and copied as an .iso.  The DVD is able to play but I cannot get the iso to play.  Any ideas?

---

### Post by carloslosgrande on 2007-07-20
I wouldn't think that an 'iso' file is a playable format for your dvd player apps.
maybe rip it as an 'avi' or something similar

---

### Post by bernied on 2007-07-20
You need to mount the .iso

Something like
```
sudo mkdir /mnt/tempdvd
sudo mount -t iso9660 -o loop /path/to/the/iso/file /mnt/tempdvd
```

[EDIT]You maybe don't need the '-t iso9660' part[/EDIT]

Then, try to play from the location /mnt/tempdvd

---

### Post by wormser on 2007-07-20
> **bernied said:**
> You need to mount the .iso

Something like
```
sudo mkdir /mnt/tempdvd
sudo mount -t iso9660 -o loop /path/to/the/iso/file /mnt/tempdvd
```

Then, try to play from the location /mnt/tempdvd

Sorry, I forgot to mention that I did mount it.  I have been trying to get it to play with VLC, but have had no success.

---

### Post by bernied on 2007-07-20
I don't know VLC, but I'm pretty sure that other players will let you play from somewhere else in the filesystem, like totem or mplayer.

---

### Post by wormser on 2007-07-20
> **bernied said:**
> I don't know VLC, but I'm pretty sure that other players will let you play from somewhere else in the filesystem, like totem or mplayer.

i have tried mplayer and ogle.  Still no luck.  Any other ideas?

---

