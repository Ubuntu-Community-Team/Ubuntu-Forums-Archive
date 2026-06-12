---
title: "does anyone know how to install mame or kmame ?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-08-06
I've installed kmame via add/remove and I kepp getting the error that the exutble file not found
I've add the file in the "folders" - but still get that error
I've downloaded some other source packages but have a no idea how to install them
I've done "make install" but got some errors after 1 hour of compiling

please help me step by step how to
from were to download , etc...
I just lost.

---

### Post by Zweih on 2006-08-06
Well, you can install x-mame from the repos with

```
sudo apt-get install xmame-common
```

Alternatively, you can go into synaptic and get it from there.

---

### Post by MaximB on 2006-08-06
1.I've installed xmame as you said - but I cannot find it now 
I've searched the system for xmame but didn't find it
2.before that I've installed kxmame I've done as I've said above but I get this massage :
"No xmame/xmess executables defined"
and I don't find the files it need.
help ?

---

### Post by MaximB on 2006-08-06
sorry - I still need help

---

### Post by DoktorSeven on 2006-08-12
Actually you need more than xmame-common.

I would think that xmame-common would already do so, but in case it did not, install either -- or both of:
[b]xmame-sdl
xmame-x[/b]

These are both installed in /usr/games/ as:
[b]xmame.SDL
xmame.x11[/b]

So when you run kxmame or gxmame (run kxmame, it seems to be more stable, at least to me), in the Directories option under the first tab, browse to /usr/games/ and select whichever one of the binaries you installed, then *make sure you hit **Add** under Browse* when you select the binary.  (If you want to use both binaries, browse to then Add the other.  Doesn't hurt.)

The executables added then should show up under the Executables option.  

You then set your rom directory under the directories option, "rebuild game list" under Options if k/gxmame hasn't already done so, then hit the Refresh button to have it look for available ROMs in your selected directory.

---

### Post by MaximB on 2006-08-12
thanks
the cps2 roms work good
but the neo-geo doesn't work
it says that some files are missing from the rar file
is there other emulator for neo-geo games that work under linux ? with a GUI ?

---

### Post by BoyOfDestiny on 2006-08-12
> **MAXDDARK said:**
> thanks
the cps2 roms work good
but the neo-geo doesn't work
it says that some files are missing from the rar file
is there other emulator for neo-geo games that work under linux ? with a GUI ?

Well you are probably missing the neogeo bios. Google for it.

As for gui, I like using advmenu and advmame.

[http://advancemame.sourceforge.net](http://advancemame.sourceforge.net)

Anyway, works great:

---

