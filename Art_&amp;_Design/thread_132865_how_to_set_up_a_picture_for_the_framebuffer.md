---
title: "how to set up a picture for the framebuffer?"
date: 2006-02-19
forum: Art &amp; Design
---

### Post by aslocum on 2006-02-19
Hi all,

i dont want usplash, bootsplash, splashy or whatever.. i just want to set a background picture to my frambuffer console.
anyone know how to do this?

---

### Post by kaamos on 2006-02-19
I don't think this can be done in any simple way. Suse has this, and I think that runs on a separate Xserver or something..

---

### Post by chadwick359 on 2006-02-20
It isn't a seperate Xserver, because the images are up way before X is even being thought about in the load process, Suse uses splashy, if i remember correctly, and it's requires kernel patching to get working. I looked into it long ago, but decided that it wasn't worth it. Sorry, but that's as much help as I can really give.

Edit. Correction on this, Splashy is userspace, and doesn't need a kernel patch. I'm still not sure 100% if that is what Suse is using.

---

### Post by pestilence on 2006-02-23
Actually this started as a Gentoo project under the name Bootsplash. It required Kernel patching (it ain't that hard to do) but the last time i used it (when i was still a part of the Gentoo community) it was a bit slow.
The rest of the tools, i've never heard them...but i think i'll give them a shot ;)

---

