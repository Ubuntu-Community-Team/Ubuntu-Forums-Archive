---
title: "Rage 128 Ultra on G3 Imac and 3D Rendering aka  DRI"
date: 2007-02-27
forum: Apple PPC Users
---

### Post by duamau on 2007-02-27
Anyone here know how to make DRI and 3d acceleration work with a Rage 128 Ultra on an Imac? I figured out from other posts that it is necessary to coment out DRI in the Xorg.conf file to even get the card to run. That is great, but I want to run BZflag and Torqs. These require 3D acceleration. Any help will be greatly appreciated.

---

### Post by tgalati4 on 2007-02-27
What is the output of:
glxgears -printfps

I think the Rage 128 has limited 3D capability.  How much video RAM is available?  You might have to drop resolution and/or go to 16-bit color to free up enough video RAM for 3D to work properly.

---

### Post by linear on 2007-03-05
A possible fix is described in this thread: [http://www.ubuntuforums.org/showthread.php?t=191080](http://www.ubuntuforums.org/showthread.php?t=191080).

I haven't tested it myself.

---

