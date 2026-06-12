---
title: "Whats a good avi player"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-04-18
Whats a good avi player for Ubuntu i dont like the ones that have 2, 3, 4 windows pop up just one with the Window for the movie. Please help me find one



                                                                    DOWN WITH MICROSOFT

---

### Post by taurus on 2007-04-18
vlc and it is in the repos.

```
sudo aptitude update
sudo aptitude install vlc
```

---

### Post by microsoft92sucks on 2007-04-18
thanks man that one is working great

---

### Post by taurus on 2007-04-18
Glad you like it.

---

### Post by Fuzzgun on 2007-04-19
Hi,
I've just installed VLC and I am getting video but not audio with any type of movie file (avi, wmv, mpeg, etc..).
I've been getting the same problem with Mplayer and Kaffeine but for some reason they work perfectly with Totem (also plays wma files).

Any ideas?

---

### Post by mand0 on 2007-04-19
> **Fuzzgun said:**
> Hi,
I've just installed VLC and I am getting video but not audio with any type of movie file (avi, wmv, mpeg, etc..).
I've been getting the same problem with Mplayer and Kaffeine but for some reason they work perfectly with Totem (also plays wma files).

Any ideas?

How exactly did you install VLC?

Go to add/remove programs and search for "mp3" and install "Gstreamer extra plugins" "Gstreamer ffmpeg video plugin" and "ubuntu restricted extras"

---

### Post by aktiwers on 2007-04-19
Check this out..
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Fuzzgun on 2007-04-21
> **mand0 said:**
> How exactly did you install VLC?

Go to add/remove programs and search for "mp3" and install "Gstreamer extra plugins" "Gstreamer ffmpeg video plugin" and "ubuntu restricted extras"

Have updated to Feisty and installed the Gstreamer plugins and everything is working perfectly. :)

---

