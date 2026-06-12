---
title: "Opening a media file?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by TarB on 2007-07-24
How do I open a media file using the terminal? What is the command, and where can I find the list of all of these useful commands? I want to open ".avi" file using the terminal. How do I do it?

---

### Post by doomster on 2007-07-24
i dont think youre able to play an avi through pure terminal.youre able though to run any program installed, even media players, typically by typing their name(EX. kaffeine/mplayer/audacious)

---

### Post by Nekiruhs on 2007-07-24
Well, VLC has an ncurses terminal CLI interface. install VLC (sudo apt-get install vlc) then run it with vlc -I ncurses I am using it right now and it is amazing.

---

### Post by RomeReactor on 2007-07-24
Hi. If you have mplayer installed, try it like this:
```
mplayer /PATH/TO/FILE.avi
```
Same with Totem.

---

### Post by distroman on 2007-07-24
> **TarB said:**
> What is the command, and where can I find the list of all of these useful commands?

```
man mplayer
```

gl :)

---

