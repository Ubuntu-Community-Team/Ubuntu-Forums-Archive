---
title: "help!"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-26
How do I uninstall gaim beta and reinstall the gaim that came with ubuntu? i had file sharing set in the original gaim then i installed the beta and file sharing doesnt work. i dont want the beta anymore. how do i revert to the gaim that came with ubuntu?

---

### Post by woedend on 2006-06-26
go to system, adminisration, synaptic.

uninstall gaim and gaim-data if they are installed.
this may remove ubuntu-desktop if you havent already removed it.  Thats ok.
then, after theyve been removed, reinstall gaim from the repos the same way(click them and mark for installation).  If you have manually added a repo for gaim beta, make sure to remove that first.  If you just downloaded and installed the file, this will work fine.  After you are finished, if you want ubuntu-desktop back, simply search for it and mark it for installation after gaim is installed.
HTH

---

### Post by maddbaron on 2006-06-26
it will uninstall ubuntu-desktop? so what will my desktop be? *confused* i installed it from automatix, ok i found it in synaptic darn it wants to remove desktop....this is annoying...

---

### Post by woedend on 2006-06-26
no maddbaron this is ok.  Ubuntu-desktop is not ubuntu.  It's hard to explain, but ubuntu-desktop is just a tiny tiny file that tells synaptic and apt all the programs that come with ubuntu.  Removing it does NOTHING bad for the time being....everything is still there.  Just remove gaim, let it remove ubuntu desktop.  after you reinstall gaim, search for ubuntu-desktop and install it.  No problems - promise :)

---

