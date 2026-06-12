---
title: "[SOLVED] Control Volume From Terminal ?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-08-22
I am looking for some *command* that would control the volume output of my speakers. It can't be nothing graphical like alsamixer, as you can not use a command to set the volume, I don't think.

I want to use this for a crontab to automatically adjust my volume to a certain output at a certain time. Anyone know how to do this?

Dr Small

---

### Post by deadgobby on 2007-08-22
I think this is what you are looking. Man ASLAmixer is  easy, but hey command lines are all ways good.
[http://www.linuxforums.org/applications/sox__the_commandline_audio_workstation.html](http://www.linuxforums.org/applications/sox__the_commandline_audio_workstation.html)

---

### Post by raijinsetsu on 2007-08-22
Just use amixer. Here's the man page for it: [--LINK--]("http://linux.die.net/man/1/amixer")
It will let you run something like "amixer MASTER_CONTROL VOLUME_LEVEL"

---

### Post by schorsch on 2007-08-22
To fully turn down the master volume use this:
```
amixer set Master 0
```

---

### Post by kerry_s on 2007-08-22
> **schorsch said:**
> To fully turn down the master volume use this:
```
amixer sset Master 0
```

you got a extra "s" there

amixer set Master 0%
amixer set Master 50%
amixer set Master 5+%
amixer set Master 5-%
etc...

---

### Post by schorsch on 2007-08-22
Ups, sorry ... just edited the post. Thanks!

---

### Post by Dr Small on 2007-08-22
Thanks guys. I will have to try this out :)

---

### Post by Dr Small on 2007-08-22
I had to change Master to PCM, but I got it to work! Thanks fellas :D

Dr Small

---

