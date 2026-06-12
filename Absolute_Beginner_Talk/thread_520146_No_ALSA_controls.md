---
title: "No ALSA controls"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-08-07
I just updated the ALSA drivers, library, utils, and oss.

For some reason I'm unable to control the volume at all on the computer (it's permanently at 100%)

Could this be from faulty utils ?
I ask this because I was unable to make or make install the utils while manually updating.

Could it be fixed if I installed an older version of Utils?

---

### Post by nitro_n2o on 2007-08-07
can you change anything using the command alsamixer from the terminal

---

### Post by kbsuperstar on 2007-08-07
I can make the controls go down, but the volume stays the same.

---

### Post by kbsuperstar on 2007-08-07
It appears there isn't a "makefile" in the utils dir after unpacking and configuring.

I see two files labeled "makefile.am" and "makefile.in" but when I do "sudo make" it says there is no makefile...


I'm thinking that the Utils is the reason that I can't control the volume.

Any ideas ?

---

### Post by Happy_Man on 2007-08-07
If they worked before the update, then you can always go back to the previous version. Better what you know then what you don't.

---

### Post by kbsuperstar on 2007-08-07
The problem with that option is that the original version I had couldn't produce volume very loudly (it was quite quiet).

I find it weird that I can control the PCM but not the Master Volume.

Maybe it's a clue to the solution?

---

