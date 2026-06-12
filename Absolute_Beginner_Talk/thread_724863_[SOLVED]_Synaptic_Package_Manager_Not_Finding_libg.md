---
title: "[SOLVED] Synaptic Package Manager Not Finding libgtk2.0-dev?"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by navraj on 2008-03-15
I'm new to ubuntu (and to linux), so I'm not sure if I'm expecting the right think from synaptic package manager. Basically, I want to install wxGTK on my ubuntu gutsy 7.10. For this, I need the development libraries for GTK+, preferably version 2. So, I went looking for the libgtk2.0-dev package, but the package manager doesn't find it, even after reloading the package list. 

I see the package is available on the ubuntu website, but manually installing it requires other packages to be installed first...I tried going that route but some package or another was needed for everything. Is there any automated way to install all the packages needed for libgtk2.0-dev and then install libgtk2.0-dev itself?

Thanks!

---

### Post by wormser on 2008-03-15
libgtk2.0-dev is in Synaptic.  Sounds like you need open up the repositories.  System> Administration> Software Sources.  Make sure the Universe and Multiverse repositories are enabled.  Then search Synaptic for libgtk2.0-dev.  The dependencies will automatically be selected for download.

---

### Post by navraj on 2008-03-15
Thanks for that info, it brought me one step closer. I can see many more libraries now, but I still can't see libgtk2.0-dev. I found libgtk1.2-dev, but for the latest version of wxGTK I think I'd want libgtk2.0.

Here is the link for the package...I didn't see any notes regarding it being made obsolete, so I'm not sure why synaptic is not finding it.

[http://packages.ubuntu.com/gutsy/libgtk2.0-dev](http://packages.ubuntu.com/gutsy/libgtk2.0-dev)

Any suggestions?

---

### Post by navraj on 2008-03-15
Nevermind, I also checked the main repository and libgtk2.0-dev showed up afterall. Thanks!

---

