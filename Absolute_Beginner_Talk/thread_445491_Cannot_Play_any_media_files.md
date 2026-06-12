---
title: "Cannot Play any media files"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by StevenP9891 on 2007-05-16
I downloaded and installed the packages and plugins for both totem and mplayer for the firefox web browser. Yet when I try to stream a wmv, quicktime, or real video formats i can't. Also when i download videos it opens it in "Movie Player" yet gives me an error message saying that i need additionsl plugins. I really need some help.

---

### Post by Gmbrdilos on 2007-05-16
did you try this?
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by StevenP9891 on 2007-05-16
Yea, i downloaded all of it- same problems

---

### Post by BHelts on 2007-05-16
which version of Ubuntu are you using?

---

### Post by StevenP9891 on 2007-05-16
7.04

---

### Post by BHelts on 2007-05-16
have you tried installing ubuntu restricted extras?

make sure all repositories are enabled

```
sudo apt-get install ubuntu-restricted-extras
```

or add-remove programs

or synaptic

---

### Post by StevenP9891 on 2007-05-16
Yea, I downloaded and installed everything- still nothing. wat do you think could be wrong??

---

### Post by BHelts on 2007-05-16
totem (movie player) and mplayer do not play very well together.  go to /usr/lib/firefox/plugins and delete all the files that have libtotem in the name.  see if that helps.

---

### Post by StevenP9891 on 2007-05-16
YEP!!! that did the trick. Thanks for all your help

---

### Post by StevenP9891 on 2007-05-16
Actually, i've got another problem. I can see the video stream but there no navigation bar (play, pause, seek ,etc.)

---

### Post by StevenP9891 on 2007-05-16
did everyone abandon me???

---

### Post by BHelts on 2007-05-16
sorry bout that, took a little nap overnight.
the navigation buttons missing is a new one to me.  is it with every kind of stream or one stream in particular?  only audio streams, only video streams or both?

---

