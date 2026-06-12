---
title: "Help Graphic Resolution   Ubuntu 7.10"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by mr_manson on 2007-10-20
Hi

I've update my system with update mangaer from 7.04 and after it all was ok...but i think i've made some big mistake to try to remove firefox and other application like gnome desktop i think  (not sure) so after reboot at now my graphic card has only 640 x 480 resolution ?!??!?!

What can i do to verify what important component maybe i removed and reinstall it ?

Thanks a lot

:confused:

---

### Post by Perfect Storm on 2007-10-20
Try
```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install gnome-desktop
```

Also you can check synaptic history to see which package you have installed/removed so you can install them again.

---

### Post by mr_manson on 2007-10-20
Hi
Thanks for your reply
I try to make what you told me but never change i just see maybe there is a problem to recognize teh correct monitor type...but it's a notebook...so i think i'll try to reinstalll completely ubuntu :rolleyes:

---

