---
title: "Flash has no sound"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-11-29
I have the Flash 9 plugin for firefox, but I can't get the sound to work half the time.  Why would it just randomly work?  And is there a way to fix it?

---

### Post by OptimusPrime on 2006-11-29
Should I just reinstall the flash plugin?

---

### Post by LexAevum on 2006-11-29
I don't think a reinstall would help.
Sadly, there seem to be some serious problems. Do a search for "flash" and see what you come up with.
I'm stuck with a functional flash that is constantly rejected by most flash detect scripts.
I'm so tired of seeing "you need flash 9 to view this page!"](*,)

---

### Post by LexAevum on 2006-11-29
OMG I fixed it!

Ok, try this....
get flash-player-plugin-9.0.21.78 and untarwhatever it until you can get the libflashplayer.so out of it.

Open a term and "locate libflashplayer.so"
Manually replace every single copy you found with the one you just got out of the flash-player-plugin-9.0.21.78.tar.gz (make sure all browser windows are closed and that you have permission to overwrite the file locations in question) if you have trouble with the overwrite, use sudo cp from the terminal. Ie:
$ sudo cp '/home/(user)/downloads/flash-player-plugin-9.0.21.78/libflashplayer.so' '/some/other/place/you/found/one/libflashplayer.so'

---

