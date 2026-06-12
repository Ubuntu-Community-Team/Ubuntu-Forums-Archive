---
title: "Amarok .wma problem"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by firebirdworks on 2007-02-01
When I tried to play a .mp3 amarok lead me to a download screen.  But when I tired to play a .wma it would not play it.  It just automatically said that the playlist was done.  Can anyone help.  If there is no way to play it, than can someone direct me to a ubuntu supported mp3 conversion problem.

---

### Post by muguwmp67 on 2007-02-01
Have you installed the codecs you need?

See:
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs]("https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs")

---

### Post by psyne on 2007-02-01
Is the WMA file DRM protected content? If so then to the best of my knowledge you won't be able to play it without stripping the DRM protection from the file.If it is not have you installed the w32codecs.

```

wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
sudo dpkg -i w32codecs_20061022-0.0_i386.deb

```

---

### Post by firebirdworks on 2007-02-01
No, I didn't dowload them.  Thanks alot.

---

