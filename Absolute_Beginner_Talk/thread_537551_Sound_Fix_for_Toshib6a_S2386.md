---
title: "Sound Fix for Toshib6a S2386"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by dirtblack on 2007-08-29
I am new to Ubuntu.  I have installed on my Toshiba S2386.  After reading the forums there is a sound fix.  To fix the sound I need to edit the alsa-base file.  When adding the required line I can't save the file. Ubuntu says that I don't have file permissions to save it.  Any help greatly appreciated.

---

### Post by ThrobbingBrain66 on 2007-08-29
You have to open the file using 'gksudo'

```
gksudo /etc/modprobe.d/alsa-base
```

---

### Post by dirtblack on 2007-08-30
I do appreciate your help.  I ran that in terminal and nothing happens. I do get a prompt after it runs but that's it.

---

### Post by ThrobbingBrain66 on 2007-08-30
arg, I'm sorry,  I meant to write
```
gksudo gedit /etc/modprobe.d/alsa-base
```

---

### Post by dirtblack on 2007-08-31
Many thanks!!  Works now.  So far I'm impressed with Ubuntu.

---

