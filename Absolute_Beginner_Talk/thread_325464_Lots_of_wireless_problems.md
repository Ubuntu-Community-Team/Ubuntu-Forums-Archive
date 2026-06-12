---
title: "Lots of wireless problems"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by Ronfar on 2006-12-25
I need to get Network-manager-gnome installed so can someone point me in the direction to get that package? Whenever I try to install the one I found now I get errors like this 

  Depends: libatk1.0-0 (>=1.12.1) but 1.11.4-0ubuntu1 is to be installed
  Depends: libavahi-client3 (>=0.6.13) but 0.6.10-0ubuntu3.3 is to be installed

and they go on for awhile. My guess is that is an edgy package and I need one for dapperdrake. I've probally read the whole archive on my wireless card trying to get it fixed and this seems to be the last thing to try, so if anyone can help me I'd apperciate it.

---

### Post by Azakus on 2006-12-25
Try installing with aptitude
```
sudo aptitude install network-manager-gnome
```

---

