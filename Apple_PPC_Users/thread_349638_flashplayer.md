---
title: "flashplayer?"
date: 2007-01-30
forum: Apple PPC Users
---

### Post by h.ornstein on 2007-01-30
I found a post on the Gentoo forums from 2003! Someone mentioned the possibility of installing flashplayer with "qemu", a piece of software. If you have tried it, please let us know.

---

### Post by hal10000 on 2007-01-30
Are you talking about flashplugin or flashplayer? 
If you mean flashplugin then just install the package flashplugin-nonfree, you'll get the latest flash9 plugin.

---

### Post by maxamillion on 2007-01-30
> **hal10000 said:**
> Are you talking about flashplugin or flashplayer? 
If you mean flashplugin then just install the package flashplugin-nonfree, you'll get the latest flash9 plugin.

That package currently isn't supported for the PowerPC processor architecture and I assume (because of what category the thread was posted) that is what h.ornstein is using.

h.ornstein: I used to have an iBookG4 (just sold it 2 weeks ago for money for text books for the semester) but my desktop is an AMD64 which also lacks flash support so I use the package libflash-mozplugin which is the [Gnash (GNU Flash Player)]("http://www.gnu.org/software/gnash/") package, its isn't 100% flash9 compliant and is still under heavy development, but its a step in the right direction and I believe it is currently fully flash7 compliant so it will atleast get you around the net. Its not perfect and will from time to time crash out firefox, but its better than nothing and I assume once it goes stable, life will be good.

---

### Post by hal10000 on 2007-01-30
Sorry, i did'nt notice this is th PPC category.

---

### Post by 3rdalbum on 2007-01-30
> **h.ornstein said:**
> I found a post on the Gentoo forums from 2003! Someone mentioned the possibility of installing flashplayer with "qemu", a piece of software. If you have tried it, please let us know.

Yes, I think it's possible to install Flash Player (or x86 Firefox and the plugin) using User-Mode Emulation in Qemu. You'd need a bollocksload of x86 libraries, but it should be possible.

Unfortunately, I can't find anyone who's actually done it. I want my new PPC distribution to include a GUI or an automated script to set up Qemu's UME, but first I need someone to advise me on how it's done! If you're reading this post and you've done this before, please send me a message.

---

