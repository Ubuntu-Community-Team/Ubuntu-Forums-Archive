---
title: "Ld_library_path"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by PMTUB on 2007-05-09
Where is this file stored and when is it loaded?

I am trying to install Bluetooth ALSA and it cannot find the libasound2 library which is in /usr/lib.

Thanks,

Peter

---

### Post by Kobalt on 2007-05-09
Are you compiling Bluetooth alsa ? 
libasound2 is installed by default on Ubuntu but for compiling you may need libasound2-dev (you can find it and install it from Synaptic).

---

### Post by ikonia on 2007-05-09
The linker should reference /etc/ld.so which can be edited through ldconfig and /etc/ld.so.conf.

LD_LIBRARY_PATH is not a file, its an environment varible which the OS will use in the same was as ld.so.

---

