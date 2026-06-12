---
title: "mupen64 wont open"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by ChekhovTheAnton on 2007-08-12
Hello all.  I'm having a problem opening Mupen64.  It is installed (and it's only installed because I used a custom script found on these boards).  I click on Applications>Games>Mupen64 and then nothing happens.

I have the same problem with LXDoom, even after installing freedoom and the shareware wad. But Mupen64 is the main thing I'm concerned with.

I've already fixed quite a few problems just by digging around in these forums.  It really does make using Ubuntu a lot easier, so thanks for all the help.

---

### Post by ChekhovTheAnton on 2007-08-15
Here's what I get from the terminal when I try to run it:

/usr/local/games/mupen64-0.5/mupen64: error while loading shared libraries: libSDL-1.2.so.0: wrong ELF class: ELFCLASS64

any ideas?

---

### Post by Bachstelze on 2007-08-15
Pretty self-explanatory. Mupn64 needs the libSDL-1.2.so.0 library, which is not installed on your system. So you go to [http://packages.ubuntu.com](http://packages.ubuntu.com), search for the file and it will tell you the package you need to install :)

---

### Post by ChekhovTheAnton on 2007-08-15
I already have the package installed though.  I went to Synaptic and searched for it.  I installed libsdl1.2debian-all (as well as alsa and nas) and mupen64 still had the same outcome in the terminal.  I don't think I did anything wrong in installing the packages.

Thanks for the reply, though.

---

### Post by Crube on 2007-08-15
Have you tried using another audio plugin for Mupen64?

---

### Post by Bachstelze on 2007-08-15
Are you running a 64 bit system ?

---

### Post by ChekhovTheAnton on 2007-08-15
I haven't tried using another audio plugin, and I am running a 64 bit system.

---

### Post by ChekhovTheAnton on 2007-08-17
I got it running.  Thanks for the help.

---

