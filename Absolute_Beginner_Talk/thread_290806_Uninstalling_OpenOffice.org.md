---
title: "Uninstalling OpenOffice.org"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-11-01
Hello again.

I just installed Edgy and I noticed that along with it, there are a lot of packages in Synaptic that provide drivers for various video cards. My current card is a nVidia RIVA TNT2 model, and I'm not planning to change it. Is it safe for me to remove those driver packages?

---

### Post by Joe_CoT on 2006-11-01
A good way to decide these things is to go into synaptic, search for the package in question, go to the dependencies tab, and see what it's a dependency of.

so any of those video drivers will be a dependency of xserver-xorg-video-all
xserver-xorg-video-all is a dependency of xserver-xorg
xserver-xorg is a dependency of xorg
xorg is a dependency of whatever desktop you use (ubuntu-desktop, kubuntu-desktop, etc).

Will removing those drivers break your system? No. However, all those metapackages will be removed; those metapackages need to exist for any distribution upgrade to work reasonably well (people not having their desktop package broke a **lot** of systems when people updated to Edgy Eft).

In other words, leave them alone, or remember to install your desktop package again before upgrading.

---

### Post by podunk on 2006-11-01
I may be misunderstanding your question? The packages installed on your machine will have the check box a solid green. The ones without the solid green are available to download if you need or want them.

If there is a driver installed on your machine - if it were mine I'd likely leave it on until I knew what everything did.

---

### Post by zugu on 2006-11-01
I'm sorry, the correct title for this post would have been "removing video drivers", not "Uninstalling OpenOffice.org".

However, I'll look into the dependencies and I'll see what I can do. I just don't like to have drivers around for Voodoo or Intel video cards, as long as I'm not planning to use them.

---

