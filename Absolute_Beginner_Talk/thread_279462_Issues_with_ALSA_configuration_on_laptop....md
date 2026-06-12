---
title: "Issues with ALSA configuration on laptop..."
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by DTXBrian on 2006-10-18
So... I've had Ubuntu 6.06 for less than a week, and I already know that I love it.  Nevertheless, there are two nagging issues which I cannot resolve, despite my repeated trials.  I cannot manage to get Java to work properly in the web browser, and I cannot get the sound to work on my computer at all.

Anyway, the Java can wait.  I downloaded the latest ALSA driver, library and utility sets.  From /usr/src/alsa-driver-1.0.13/ I ran "./configure"... from there, I learned I needed to download GCC and a few other tools, which apt-get install corrected.  I ran "make" and it ran a bit of a program, and then I typed "make install" and it ran fine... until the line "cp cannot stat 'snd-aloop.ko'" No such file or directory" came up.  I typed "locate snd-aloop.ko" and have discovered this file is not on my system at all.  What do I need to do to correct the issue at hand so I can get sound to my system?

Thanks, sorry I'm such a noob.

Brian

---

### Post by catanzag on 2006-10-18
For both issues you can give a look [http://ubuntuguide.org/](http://ubuntuguide.org/)

regards

catanzag

---

### Post by DTXBrian on 2006-10-18
I appreciate the direction... but the problem I'm having is that I'm just flat missing a file.  I need to know where I can get it.

---

### Post by catanzag on 2006-10-18
Oops, sorry, I suggested you that link because apt-get works very fine if you had the package already available (though I like programming...).

Back to the missing file, *snd-aloop.ko* is a kernel module, if it is not present in your computer, it is probably because it was not compiled: is there *snd-aloop.c* or something similar it the tree under the installation directory?

---

### Post by DTXBrian on 2006-10-18
I've got similar files in...

/usr/include/alsa-driver-1.0.13/drivers/aloop-kernel.c
/usr/include/alsa-driver-1.0.13/drivers/aloop.c
/usr/src/alsa-driver-1.0.13/drivers/aloop-kernel.c
/usr/src/alsa-driver-1.0.13/drivers/aloop.c

Those mean anything of great importance?

---

### Post by catanzag on 2006-10-19
Are some *ko modules that were compiled in /usr/src/alsa-driver-1.0.13/drivers directory? From a compilation/installation point of view, my primary question is if the environment is correct (linux headers and module-assistant), if other drivers were compiled, if snd-aloop.ko line is included in a Makefile somewhere and if all settings are correct, for instance, the setting of the variable CONFIG_SND_LOOPBACK.

I'm sorrybut I'm not an expert of ALSA, what I can suggest you (if you don't want to install it automatically with apt-get, sorry for my repetition, but my experience with linux is to have, firstly, a working box, and then, make some experiments) is eventually to make a new post in a more specific forum (Multimedia & Video ?), but please note that Dapper comes with ALSA 1.0.10, while you're using the latest one: I don't know if there are dependancies/incompatibilities with your kernel.

regards

catanzag

---

