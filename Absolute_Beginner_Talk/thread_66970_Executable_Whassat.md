---
title: "Executable? Whassat?"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by SevenForever on 2005-09-18
Alright, now this would seem to be easy, but I can't seem to get anywhere. I downloaded a file (Last.fm player) for linux as an executable. (Came in a .bz2 archive) when I extracted it I got a folder of images and a file called "player" with no extention. I'm assuming that's the installer, but it does nothing. Any idea what I'm doing wrong?

Thanks.

---

### Post by John.Michael.Kane on 2005-09-19
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

hope that helps..

---

### Post by Jussi Kukkonen on 2005-09-19
[QUOTE=SevenForever]Alright, now this would seem to be easy, but I can't seem to get anywhere. I downloaded a file (Last.fm player) for linux as an executable. (Came in a .bz2 archive) when I extracted it I got a folder of images and a file called "player" with no extention. I'm assuming that's the installer, but it does nothing. Any idea what I'm doing wrong?

Thanks.[/QUOTE]
 It doesn't sound like a source package, so Plisskens web page probably does not apply.
[B]
Try this in a terminal:[/B]

(you need to be in the correct directory first, ask here if you don't know how to do that)
This marks the file as executable:
```
chmod u+x player
```

This runs the file:
```
./player
```

---

