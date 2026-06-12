---
title: "How do I dump audio from an .flv clip using Mplayer?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by esocyn on 2007-02-12
I know the command goes something like mplayer -dumpaudio <insert file here>, but I get this when I do that;

> 91 audio & 204 video codecs
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing Dalebum.flv.
File not found: 'Dalebum.flv'
Failed to open Dalebum.flv


Exiting... (End of file)

Anything I'm doing wrong? What should I do differently?

---

### Post by esocyn on 2007-02-13
Anyone?

---

### Post by esocyn on 2007-02-13
At least any links?

---

### Post by mysha on 2007-02-15
The command you are looking for is:
```
mplayer -dumpaudio -dumpfile audio.mp3 Dalebum.flv
```

---

### Post by ubu-for on 2007-02-26
> **mysha said:**
> The command you are looking for is:
```
mplayer -dumpaudio -dumpfile audio.mp3 Dalebum.flv
```

Works great! Thank you very much!

Linux rules! :mrgreen:

---

