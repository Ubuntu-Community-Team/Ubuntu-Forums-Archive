---
title: "Problem mounting an ISO image"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by deggial on 2007-01-05
Hi everyone,

I am trying to mount an ISO image but I always seem to get the same error.

Cmd: sudo mount -t iso9660 -o loop ~/image.iso /media/cdrom0 (or any other directory)
Result: mount: Not a directory

I'm quite certain that all paths are valid and the directories used are indeed directories, however this problem persists. Any ideas on what might be going on?

---

### Post by Phesto on 2007-01-05
try it this way
sudo mount ~/image.iso /media/cdrom0 -t iso9660 -o loop

---

### Post by taurus on 2007-01-05
```
sudo mount -t iso9660 -o loop image.iso /media/cdrom0
```

---

### Post by Oki on 2007-01-05
Hi

You could also download Kiso [http://kiso.sourceforge.net/](http://kiso.sourceforge.net/) (look in synaptic for kiso), witch gives you a GUI for installing ISO files, much like Deamontools for Windows. Kiso can also do much more(converting).

---

### Post by deggial on 2007-01-05
Thanks for the replies. I will try out Kiso, hopefully this will solve my problems.

---

