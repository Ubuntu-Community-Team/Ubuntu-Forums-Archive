---
title: "Compile my own cd of apps, without using apt-get"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by yogo on 2007-08-09
The title says it all, I want to make a cd that has a bunch of stuff, wine etc How can I get them without using apt-get in terminal?

The pc I want to install from does not have internet connection YET and I am tired of transferring files back and fouth, I am not sure if many packages are available on the live CD and where they are on it.

Thanks

---

### Post by p_quarles on 2007-08-09
Generally it's not a good idea to compile an app on one machine *for *another machine. Wires could get crossed. If you have a machine that does have internet access, you can use the aptoncd package to make a customized repository on cd. Aptoncd will show up in your administration menu after you:
```
sudo apt-get install aptoncd
```

---

### Post by yogo on 2007-08-09
> **p_quarles said:**
> Generally it's not a good idea to compile an app on one machine *for *another machine. Wires could get crossed. If you have a machine that does have internet access, you can use the aptoncd package to make a customized repository on cd. Aptoncd will show up in your administration menu after you:
```
sudo apt-get install aptoncd
```

I tried that and got an error could not find package?


TIA

---

### Post by p_quarles on 2007-08-09
Hmm. I went to Synaptic to try to figure out which repository I installed it from, and I couldn't figure it out. Maybe I used a .deb package. 

In any case, it is available as a .deb on SourceForge:
[http://sourceforge.net/project/showfiles.php?group_id=174934&package_id=200666](http://sourceforge.net/project/showfiles.php?group_id=174934&package_id=200666)
Download the one that ends .deb, obviously, and not the one that ends in tar.gz. You will be able to install this by double-clicking on the file.

---

### Post by yogo on 2007-08-09
thanks

---

