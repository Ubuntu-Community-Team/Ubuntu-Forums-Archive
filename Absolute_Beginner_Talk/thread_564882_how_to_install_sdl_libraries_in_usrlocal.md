---
title: "how to install sdl libraries in /usr/local?"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by phatty420 on 2007-10-01
Hi, I'm having a problem with my libraries being in the wrong folder.  I need some sdl libraries that are in my /usr/lib/ folder in my /usr/local/ directory.  I installed them via synaptic, and that's where they installed them.  

Is there an easy way to do this?  I'm having a problem with libSDL_gfx libraries. 

Any other information that you think would be helpful to help you help me, just let me know.

---

### Post by jordanmthomas on 2007-10-01
```
man ln
```
Symbolic links are your friend here.

---

### Post by llamakc on 2007-10-01
You can symlink them. What program requires them in /usr/local?

---

### Post by Hospadar on 2007-10-01
it will probably be real tough to install them there manually, you could always manually extract the files from the .deb and put em where you want em.  alternatively you could build them yourself and use the ./configure switches to change the install location. (this is probably the safest choice aside from symlinks I don't know if there are hardcoded locations involved with the library that would be messed up by manually dumping them in /usr/local)

---

### Post by phatty420 on 2007-10-01
> You can symlink them. What program requires them in /usr/local?

I'm trying to get openBOR working. There are more details about it in this thread if that helps - [http://ubuntuforums.org/showthread.php?t=562931]("http://ubuntuforums.org/showthread.php?t=562931")

 I guess I'm gonna try the 'man ln' command and see where that gets me!

---

### Post by jordanmthomas on 2007-10-01
```
sudo ln -s /usr/lib/libSDL_gfx.so /usr/lib/libSDL_gfx.so.0
```
should do the trick.

(or, change the second part to /usr/local/lib/libSDL_gfx.so.0 if it really needs to be in /usr/local for some reason)

---

