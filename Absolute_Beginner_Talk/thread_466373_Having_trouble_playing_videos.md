---
title: "Having trouble playing videos"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-06-06
I can normally play videos, but I used recordmydesktop to record something. When I recorded I selected  my full screen. Now when I do:
```
tyler@ubuntu:~/Desktop$ vlc out.ogg
VLC media player 0.8.6 Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83

```
it doesn't work and gives me that. It works fine with the videos that I recorded that only take up a piece of the screen, just no the whole screen. Any ideas on how to fix this?
Do I need more swap?

EDIT: I solved it by doing
```
sudo gedit /etc/X11/xorg.conf
```
and adding
```
Option "VideoRam" "65536"
Option "CacheLines" "1980"

```
under my "device" section.

---

### Post by FleetAdmiral74 on 2007-06-06
You can try opening it up with something other then VLC, at least then you know if the problem is with the program or the file.

---

