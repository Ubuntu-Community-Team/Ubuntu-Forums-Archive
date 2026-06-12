---
title: "Visual Effects"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by aslam92 on 2008-01-19
I installed compiz fusion and I'm trying to use the visual effects.
I go into Apperance Preference and select visual effects and select custom however I keep on getting The composite extension is not available,

I tried this with the other selections and same problem.
I even updated my drivers for a graphics card which is a radeon x1300 mobility

---

### Post by wormser on 2008-01-19
I think I had that error before installing compizconfig-settings-manager.  Try installing it.

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by aslam92 on 2008-01-19
I just tried that and still not working and getting same error.
It says I already updated it

---

### Post by wormser on 2008-01-19
Take a look at this [blog]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#").  Those were two things I did to solve that error.  I cannot remember what exactly solved it.

---

### Post by 3rdalbum on 2008-01-19
> **aslam92 said:**
> 
I go into Apperance Preference and select visual effects and select custom however I keep on getting The composite extension is not available,
I even updated my drivers for a graphics card which is a radeon x1300 mobility

ATI cards require an extra program called XGL in order to be able to run Compiz.

```
sudo apt-get install xserver-xgl
```

Or just use Synaptic Package Manager to install the "xserver-xgl" package.

That package sets everything up for you, so just reboot afterwards and your 3D effects should work. Good luck.

---

