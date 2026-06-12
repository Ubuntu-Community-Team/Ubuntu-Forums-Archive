---
title: "Problem Updating totem-gstreamer-firefox-plugin"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by notrublw on 2006-08-14
totem-gstreamer-firefox-plugin will not update from 1.4.1-ubuntu4 to 1.4.3-ubuntu1.  This is because of dependencies on totem and totem-gstreamer, currently at 1.4.1-unbuntu4 and whose latest versions (I think I've correctly added all repositories) show as 1.4.1-unbuntu4.  I'm obviously doing something wrong, but what is it?  Thanks in advance.

---

### Post by MikeMLP on 2006-08-14
I ran into this a few days ago.  I think the plugin for firefox (1.4.3) does not yet exist... or something.  I fixed this by reverting everything back to 1.4.1.  I uninstalled all things gstreamer, and then marked the firefox plugin only for installation (1.4.1)  Synaptic magically changed the version numbers of all of the other pieces of gstreamer back to 1.4.1, so that they would be compatible, and installed the necessary dependencies for the plugin (the other bits and pieces of gstreamer).  So in other words, I solved this by downgrading.  At least everything works, right?

See if this works for you...

---

### Post by TooDamFast on 2006-08-15
I reverted back as well.  just uninstalled and installed the older version.

---

