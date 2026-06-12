---
title: "[SOLVED] FRESH gutsy gibbon OS fails to install mp3 codec!"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by infernus_crusher on 2007-10-26
apparently only gstreamer0.10-plugins-good is by default installed. playing mp3 in totem results in calling the add/remove program to install gstreamer extra plugins, which is basically gstreamer0.10-plugins-ugly package.

the package cannot be installed due to "unresolved dependencies" on these two packages:
libid3tag0
libmad0

both of which are not in the repository

help?

---

### Post by forestpixie on 2007-10-26
I've got this repo - [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)

they're in there

---

### Post by infernus_crusher on 2007-10-26
the repo address has been previously added into synaptic manager, but the two packages didnt show up.

also when attempting to install GStreamer Xtra Plugins, the installation fails because "the package gstreamer0.10-plugins-ugly conflict with other installed software, please remove the other packages via synaptic before proceeding". without telling me which packages are conflicting.

---

### Post by infernus_crusher on 2007-10-26
nvm i enabled everything in the preferences and apparently it worked now. thx a lot.

---

### Post by Frak on 2007-10-26
Please mark this thread as **[SOLVED]** in the **Thread Tools** menu.

---

