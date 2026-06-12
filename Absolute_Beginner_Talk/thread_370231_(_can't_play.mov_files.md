---
title: ":( can't play.mov files"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by penguinswhtouthats on 2007-02-25
i was trying to watch the elephants dream movie thing
when i got a totem error telling me i needed a decoder or something
thats when i realized i cant play mpg on my ubuntu edgy
i googled thing but got really confused or the recomendations did not work

i also, most importantly, can't view .mov files from my sandisk card, it recognizes the camera card and lets me add files to my desktop from the card but i cannot view them

:guitar:  <<cool smiley


-thanks

---

### Post by Maestro23 on 2007-02-25
Restricted Formats: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Crooksey on 2007-02-25
```

sudo apt-get update
sudo apt-get install gstreamer0.8-plugins
```

---

### Post by AndyCooll on 2007-02-25
> **Crooksey said:**
> ```

sudo apt-get update
sudo apt-get install gstreamer0.8-plugins
```

Although that might seem quick we're actually on the 0.10 plugins now so it would be installing old software. The link in Maestro23's post is the way to go.

:cool:

---

### Post by Crooksey on 2007-02-25
True, but the files should still all play

---

