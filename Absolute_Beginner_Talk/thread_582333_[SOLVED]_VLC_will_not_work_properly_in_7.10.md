---
title: "[SOLVED] VLC will not work properly in 7.10"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by chaoswings on 2007-10-19
If I just open vlc without playing a file it works just fine

As soon as I open or launch a video and use vlc to play it it's like my mouse and keyboard input is dead....I can't click on any menu items I can't pause nothing it's like it won't take any input from the keyboard or mouse.

 but the video plays just fine I just can't start/stop it or do anything to manipulate it or vlc

I've tried taking off my restricted drivers...shutting of compiz and still no change..can anyone help?

---

### Post by Pumalite on 2007-10-19
Did you clean install or do an upgrade?

---

### Post by chaoswings on 2007-10-19
totally clean install

---

### Post by mwolfer1 on 2007-10-19
I had the same problem, did a complete remove of all VLC components, removed the [www.debian-multimedia.org](www.debian-multimedia.org) repository and reinstalled from ubuntu sources. Fixed the problem.

Martin

---

### Post by Pumalite on 2007-10-19
Hummm...I can tell you vlc works fine in my Gutsy. So remove vlc totally and reinstall.

---

### Post by gmaniac on 2007-10-19
post the output of ```
dmesg 
```and of ```
cat .xsession-errors
```

---

### Post by chaoswings on 2007-10-19
FIXED thank you!


(I wonder why i didn't think of that....

---

