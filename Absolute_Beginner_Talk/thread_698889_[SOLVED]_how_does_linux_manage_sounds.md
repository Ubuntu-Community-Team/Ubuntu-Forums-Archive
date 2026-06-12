---
title: "[SOLVED] how does linux manage sounds?"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by linux5uper on 2008-02-16
Hi all,

I have recently successfully migrated to linux and the only reason I'm keeping my win partition is because of my usb audio device (m-audio jamlab) which I can't fully configure in the buntu.

The device is recognized (as USB Audio) under linux, but I can only hear output on one channel, never the other. There is no configuration utility that I know, and all these Jack/ALSA/OSS/afewmore other sound drivers are just confusing and i don't know which one to use/configure.

Can you recommend a source where I can learn how the overall system works and how I can configure externally plugged devices? It seems to be a big mess... If you've had an experience with USB audio devices I would be happy to hear about that too!

Any help is appreciated :)

---

### Post by 444 on 2008-02-16
ALSA is *the* system. OSS is the old obsolete system. Jack/esd/arts all run on top of these systems.

So ALSA is what you should be looking at. Try "alsamixer", and look for the channel you want. And don't forget simply right-clicking on the volume icon...

---

### Post by icechen1 on 2008-02-16
Linux uses ALSA(sometime OSS,on the login screen) to output sound.
They have a wiki : [http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)
Try to search on this forum,maybe someone posted how to fix it.
That's all i can find that might help you.
edit: in a terminal
> alsamixer try to see if there is a muted channel.

---

