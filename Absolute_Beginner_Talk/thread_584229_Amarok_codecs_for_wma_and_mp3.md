---
title: "Amarok codecs for wma and mp3"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-10-20
Since my fresh install of gutsy I am trying to get all of my apps back up and running.  Having trouble getting Amarok to play my music files.  I have all of the Gstreamer plugins installed as I did with Feisty. When I attempt to play a wma file it says no codec found to play this file type. When I try to play mp3's it prompts me with an installer to play the files and says to restart the app. After I restart Amarok  it prompts to install again.

Anyone?:confused:

---

### Post by NeoLithium on 2007-10-20
have you installed the w32codecs package?

---

### Post by mramsey on 2007-10-20
Nope didn't do that one...Is it in the repos?

---

### Post by Pumalite on 2007-10-20
sudo apt-get install ubuntu-restricted-extras

---

### Post by mramsey on 2007-10-20
Thanks Guys!:guitar:

---

### Post by mramsey on 2007-10-21
Ok so I got the w32codecs...no problem there. However I still am unable to play .mp3's. I get the following message (see attached).

I click on the install... it says it installed and to restart Amarok.  when I restart I get the same issue again. Anyone else having this problem?:confused:

---

### Post by forestpixie on 2007-10-21
I had to install the replacement for libxine-extracodecs 

```
sudo apt-get install libxine1-ffmpeg
```

hope that works for you

---

### Post by mramsey on 2007-10-21
:lolflag: I just found it before your post!  That was exactly it.

Thanks

---

