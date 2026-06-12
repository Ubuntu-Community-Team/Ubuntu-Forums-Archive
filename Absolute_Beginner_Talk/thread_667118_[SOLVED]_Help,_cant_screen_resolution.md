---
title: "[SOLVED] Help, cant screen resolution"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by tad1073 on 2008-01-14
ATI Rage XL graphics card, stuck with 800x600 or 640x480 edited /etc/X11/xorg.conf, but no changes occured.

---

### Post by erykroom on 2008-01-14
Install the 915resolution package.

---

### Post by LeAstrale on 2008-01-14
In Terminale/Konsole write:

>  sudo apt-get install 915resolution 

i dont know if this works, but this is the way to go about installing it.

also, hve you installed any kind of drivers for your graphics card?

---

### Post by tad1073 on 2008-01-14
I fixed the screen resolution problem using this.
```
sudo dpkg-reconfigure xserver-xorg
```

As far as drivers, no I have not installed any. i do know which drivers to install for ati rage xl.

Also, could either of you take at look at [this post](http://ubuntuforums.org/showthread.php?t=665668) to see if you two can help me with the problem.

---

### Post by RomeReactor on 2008-01-14
Hi. Your card is currently using the open source drivers; to get the proprietary drivers, go to 'System->Administration->Restricted Drivers Manager' and enable them there.

---

### Post by tad1073 on 2008-01-14
It tells me that my hardware doesn't need any restricted drivers. Also, I am looking for the repository for the emerald themes and I cant get compiz to work.

---

