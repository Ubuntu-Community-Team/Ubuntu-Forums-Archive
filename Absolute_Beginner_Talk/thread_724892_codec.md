---
title: "codec"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by andy2 on 2008-03-15
some media files cannot be played with Ubuntu's default media player, it requests that i should have the right codecs. where can i get them?please help!

---

### Post by kaboodle_fish on 2008-03-15
Have a look here: [http://medibuntu.org/](http://medibuntu.org/)

---

### Post by chips24 on 2008-03-15
try automatix.

---

### Post by forestpixie on 2008-03-15
Also open software sources in system>admin, make sure the boxes are ticked, except the source one, open the 3rd part software tab and tick the partner box

open a terminal 

```
sudo apt-get install ubuntu-restricted-extras
```

as kaboodle says use medibuntu, as far as automatix goes - others have had problems with it in the past, but I'm only passing on information I've read here - I've never needed to use.

---

### Post by sayakb on 2008-03-15
Install all gstreamer plugins that you can find.. (the good, bad, ugly sets etc.)

---

### Post by Sef on 2008-03-15
Read [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by ubuntu27 on 2008-03-15
Hello Andy, welcome to the forums. 
What you need to do is to isntall some codecs. Check out the [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") page.
It tell you about how to install restricted (non-libre) codecs.

Check our some other pages in my signature, I am sure it will be helpful to you. Specially the one on " How-to Install Apps/Software in Ubuntu"

---

### Post by dastasha on 2008-03-15
VLC player works for me, plays just about everything.

Find it under System/Administration/Synaptic Package Manager

---

