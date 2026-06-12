---
title: "Extracting music from MTP device?"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by VoXoM on 2008-01-20
Hey, I have a Samsung YP-U3 and I'm wondering how to extract the songs from it onto my hard drive. Can anyone help? Thanks.

---

### Post by xdarkxanarchyx on 2008-01-21
You should be able to simply plug it in, if nothing pops up, check the side pane in Nautilus and it should say something there. Or in Rhythmbox. If that doesn't work for you then you'll have to mount it manually. ```
 sudo mkdir /media/mp3player (or whatever you want to call it)
sudo mount /dev/sda1 /media/mp3player (if you have a SATA drive try "sdb1") 
```
Then open nautilus and drag the files over. Or ```
 cp /media/mp3player/* ~/home 
``` Not sure if you'd need sudo for this.

---

### Post by oodledoodle on 2008-01-21
shouldn't need sudo as you should have write permissions for your own home folder.

---

### Post by xdarkxanarchyx on 2008-01-21
I've had problems *writing* to my mp3 player before without using sudo depending on how I mounted it.

---

