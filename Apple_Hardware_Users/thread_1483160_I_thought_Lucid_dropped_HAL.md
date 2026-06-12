---
title: "I thought Lucid dropped HAL???"
date: 2010-05-14
forum: Apple Hardware Users
---

### Post by JoeMac42 on 2010-05-14
I have been trouble-shooting a hardware issue on a G4 Powermac with a clean install of Lucid when I just realized that HAL is installed (version 0.5.14-0ubuntu5).  I thought the HAL package was supposed to go away in Lucid and that UDEV would be used instead.  I appear to still have both hal and udev packages installed.  Is this just a peculiarity of the Lucid PowerPC port?

---

### Post by kosumi68 on 2010-05-14
I believe this is just a good example of what always happens when one wants to phase out one technology in favor of another, presumably better one. It... takes... forever. Backwards compatibility is not only important, it may be the only way. :-)

(For other examples currently in play: upstart, pulse/oss/alsa, pidgin/empathy, xterm/gnome-terminal, what not.)

---

### Post by screaminj3sus on 2010-05-14
Just remove it, my system had hal installed and I went to synaptic and removed it, it didnt say anything else had to be removed or anything either, and my system works fine.

---

### Post by heldal on 2010-05-15
hal, hal-cups-util and the libhal development packages can be removed. But libhal1 and libhal-storage1 can not be removed from lucid due to dependencies with gnome-desktop components.

---

