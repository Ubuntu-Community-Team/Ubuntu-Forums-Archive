---
title: "GStreamer Problems"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by nebu on 2008-02-15
when i try to play any audio files or change the volume i get this error.....

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

uptill a few days ago it was workin perfectly.... but something has conked off now......

how do i configure the gstreamer??:confused:

---

### Post by billgoldberg on 2008-02-15
did you try to reboot/restart x?

Might fix it.

Reinstall the gstreamer codecs might also work or use other ones.

---

### Post by bionicyeti on 2008-02-15
I had the same problem. I had to install the newest alsa (1.0.16) drivers to get my sound back.

---

### Post by nebu on 2008-02-15
how do i do install these drivers???

---

### Post by nebu on 2008-02-15
bilgoldberg that doesnt seem to work....

---

### Post by bionicyeti on 2008-02-15
I used lswest's intructions in this thread but downloaded the 1.0.16 drivers instead. Also I had to reboot after. [http://ubuntuforums.org/showthread.php?t=623118]("http://ubuntuforums.org/showthread.php?t=623118")

---

