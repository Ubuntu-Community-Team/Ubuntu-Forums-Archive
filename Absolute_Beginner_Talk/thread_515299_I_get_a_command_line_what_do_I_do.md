---
title: "I get a command line what do I do?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by safora on 2007-08-01
So this probably sounds REALLY dumb but here goes!!

I've used Ubuntu for a few months with the GUI and decided to install the server version with LAMP option

This all works ok and I logged in

I even tried pinging websites which seem to work but I still only have a CLI and dont know how to get a GUI?

I tried the ctrl alt F keys but still stays as a CLI and I cant see any information about this anywhere
:confused::confused::confused:
Please help!

Thanks

sa-fora

---

### Post by Happy_Man on 2007-08-01
You have to install a distro package. Just type this in to a terminal prompt:

For Ubuntu: ```
sudo aptitude install ubuntu-desktop
```

For Kubuntu: ```
sudo aptitude install kubuntu-desktop
```

For Xubuntu: ```
sudo aptitude install xubuntu-desktop
```

Any one of these will give you a GUI. Just choose the one you want and install away! And if you want a command-line web browser.... ```
sudo apt-get install lynx
```

---

### Post by apswartz on 2007-08-01
I have never used the Ubuntu server version, but the ones I do use do not install GUIs. If you want a GUI you will probably need one. Try...
sudo apt-get install gnome
or
sudo apt-get kubuntu-desktop

---

### Post by safora on 2007-08-01
Thanks for that is working great!!:):):):):):):)

---

