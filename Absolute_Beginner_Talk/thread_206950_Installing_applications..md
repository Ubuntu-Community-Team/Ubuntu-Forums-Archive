---
title: "Installing applications."
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by Just4 on 2006-06-30
I know there was a tutorial somewhere on how to install applications manually and convert .rpms to ubuntu compatible packages, anyone have the link to the tutorial on how to install applications? Also, how would I go about installing QEMU and GoogleEarth under Ubuntu?

---

### Post by batholith on 2006-06-30
> tutorial somewhere on how to install applications manually and convert .rpms to ubuntu compatible packages,

Try downloading this user guide,  [http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf]("http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf") it's a pretty good general overview and covers converting .rpms...

Just keep in mind, without using apt-get or synaptic you'll have to resolve you're own dependency issues...

> how would I go about installing QEMU and GoogleEarth under Ubuntu?

I'm not sure what QEMU is, but see this thread for GoogleEarth:

[http://ubuntuforums.org/showthread.php?t=195382]("http://ubuntuforums.org/showthread.php?t=195382")

---

### Post by invalid on 2006-06-30
If I remember correctly. qemu is available in the universe repos.
```
sudo apt-get install qemu
```

---

### Post by user1397 on 2006-06-30
[quote=invalid]If I remember correctly. qemu is available in the universe repos.
```
sudo apt-get install qemu
```[/quote]always remember to update before installing, e.g, ```
sudo aptitude update && sudo aptitude install qemu
``` 
the wonderful guide for installing anything on ubuntu is found in my signature (the one called "installing anything")

---

### Post by Just4 on 2006-07-01
Ah, ok. - Is there a GUI out for QEMU on Linux? (I know there is a few available on Windows, but I'd rather stay away from Windows at the moment)

---

### Post by aysiu on 2006-07-01
If you need a GUI, there's a GUI for VMWare.

[Make sure you have extra repositories](http://www.psychocats.net/ubuntu/sources) and then ```
sudo aptitude update
sudo aptitude install vmware-player
``` For Google Earth, try [this](http://www.ubuntuforums.org/showpost.php?p=1138374&postcount=24).

---

