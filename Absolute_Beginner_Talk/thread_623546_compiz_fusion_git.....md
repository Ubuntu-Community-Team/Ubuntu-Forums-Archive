---
title: "compiz fusion git...."
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by patchido on 2007-11-26
how do i install this thing... is there any easy guide??? ive found lots of them but they say u need terminal skills which i lack... (looking where to learn them... suggestions accepted) so anyone have a easy guide on how to ???

---

### Post by patchido on 2007-11-26
[http://wiki.opencompositing.org/Install/PluginsFromGit]("http://wiki.opencompositing.org/Install/PluginsFromGit")
that is the link and i really dont think i can follow that

---

### Post by GSF1200S on 2007-11-26
It should be fairly easy without the command line if you are on 7.10.

Open up Synaptic Package Manager and search for compiz. When it comes up, install compiz-core, compiz-gnome, and both compiz fusion plugins, as well as compizconfig-settings-manager,

Of course you should make sure 3d accel is working of course. There are plenty of ways to make sure it loads at boot, but to tinker with it type:

```
compiz --replace
```

in a terminal, and you should be cubin' away. Let us know if you have any problems...

**EDIT** To play around with all of compizs options, hit alt+f2 and type:

ccsm

This will bring up the advanced desktop settings manager. If you want just basic effects, try to install gnome-compiz-manager from synaptic...

---

