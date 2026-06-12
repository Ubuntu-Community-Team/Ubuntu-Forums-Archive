---
title: "REmoving nVidia drivers"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by corowakid on 2007-10-29
I'm attempting to use Envy to load drivers for Ubuntu 7.10, and have a problem. Envy stresses that you must delete all existing nVidia drivers before proceeding. Envy will then install the drivers. I've already installed all repositories as detailed in the Envy howto.

Anyone here know what command(s) I need to use to do this? Is it something like "Purge?".

Not sure how to compile the entry, so any help would be appreciated.

---

### Post by corowakid on 2007-10-29
<Bump>

Any help anyone? Thanks

---

### Post by jaybombalous on 2007-10-29
u open up envy and check the uninstall option.

Application> system tools > envy

---

### Post by FredB on 2007-10-29
You don't need envy to install nvidia drivers on gutsy gibbon aka 7.10.

Restricted manager tool do this for you.

---

### Post by skymera on 2007-10-29
restriced manager broke my system.

envy works a beaut!
reccomended highly!

sorry  idont know the link :(

---

### Post by erginemr on 2007-10-29
That depends on how you installed nvidia drivers (from synaptic or from the installer on their site). If you i&#351;nstalled them from synaptic, you should uninstall Nvidia packages by 
"sudo aptitude remove nvidia-glx"
restart and try to install it via envy once again.

---

