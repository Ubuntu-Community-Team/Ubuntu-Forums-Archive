---
title: "My sound is gone"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by jctaft on 2007-01-16
I just got Ubuntu up and running yesterday, and I am positive that when I first installed it my sound worked because I remember hearing an African drum beat when it started.  The only thing I've done that is at all sound-related is that Iinstalled some plugins for gstreamer so that I could hear my mp3's, and my sound does not work now.  I know that my speakers and sound card work, because I can boot up in windows and it works fine, and yes my volume is turned on.  I can tell that  the movie player thinks the sound is on because I get all the wavey animations when it plays an mp3.  In my microsoft-induced computer illiteracy, I don't even know where to start, and I can't find help in any documentation, although most of it is too technical for me at this point. 

Any ideas (in regular-guy language please)

Jeff

---

### Post by NeoLithium on 2007-01-16
Open up a terminal window, then type this in:
```

alsamixer

```
And turn up all the volumes inside the program. That's how I had to get mine to work after the codecs and whatnot got installed.

---

### Post by jctaft on 2007-01-16
Didn't help, the volume was already up

---

### Post by jctaft on 2007-01-16
Nevermind, with a red face, I have to admit I was only looking at master volume.  doh!!

thanks for the help.

---

### Post by NeoLithium on 2007-01-16
No problem :)  Glad I could help

---

