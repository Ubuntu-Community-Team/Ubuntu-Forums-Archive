---
title: "Updating Rhythmbox?"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by Deaf_Head on 2005-12-22
I'd like to get the newer release because of podcast support .. but wasn't sure how exactly to do that. 

Synaptics package manager doens't seem to have any alternate installation or newer one listed?

---

### Post by shenki on 2005-12-23
I'm currently trying to compile rhythmbox cvs myself - I finally, after 4 months of trying, have got sound working on my laptop with Intel HD audio - and I'm having troubles because it seems pkg-config doesn't know about the existance of totem. (hmm, its funny how writing things out often makes you remember the soltion...time to install totem-xine :)

Anyway, in a search of the forums I stumbled across this page [http://www.banditshome.net/](http://www.banditshome.net/) with some ubuntu packages on it, including rhythmbox: 

```
wget [http://www.banditshome.net/packages/breezy/rhythmbox_0.9.2-1_i386.deb](http://www.banditshome.net/packages/breezy/rhythmbox_0.9.2-1_i386.deb)
sudo dpkg -i --force-overwrite-dir rhythmbox_0.9.2-1_i386.deb
```

(the force part is to fix up a conflict with gnomebaker, if it's installed)

Goodluck.

---

