---
title: "pics off camera in fluxbox???"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by fuscia on 2005-12-15
i gnome, as soon as i plug my camera in, i get a thing on the desktop i can click and i'm fine. in fluxbox, when i plug my camera in, nothing appears on the desktop. so, how would i get pics off my camera in fluxbox?

---

### Post by joshuapurcell on 2005-12-16
I'm not sure what is automatically putting the camera drive icon on the desktop while using Gnome, but you should still be able to see the camera drive mounted in either the /media or /mnt directories (one or the other... not sure which one). When you plug in your camera, what do you see in those directories?

You can also see what is mounted on your system by issuing this command:> mount
That will show you every filesystem that is mounted in your system, so do a before and after and see what (if anything) changes when plugging your camera in under fluxbox.

If you don't see any changes, then boot up in Gnome and run through the same steps to see what the differences are.

---

