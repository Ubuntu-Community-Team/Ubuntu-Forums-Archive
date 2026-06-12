---
title: "[SOLVED] No window decorations with compiz on nvidia"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by lamalex on 2007-12-25
I just upgraded my secondary pc to Gutsy, which has an nvidia 7600GT. Both Beryl and Compiz (before the merge) worked great on it, however in Gutsy I have no window decorations when I enable compiz-fusion. Here is the relevant section of my xorg.conf.
```

Section "Device"
        Identifier      "nVidia Corporation G70 [GeForce 7600 GT]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "DRI"           "True"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

```
Anyone have any ideas for getting it working?

---

### Post by PmDematagoda on 2007-12-25
Go to the Advanced Desktop Effects and Settings and enable the Window Decoration feature.

---

### Post by lamalex on 2007-12-25
Wouldn't it be awesome if it were that easy? No dice. I've tried that already.

---

### Post by PmDematagoda on 2007-12-25
Did you try purging Compiz and reinstalling it?

---

### Post by lamalex on 2007-12-25
What is this, windows?

EDIT: Reinstalling / purging was not necessary (as it really never should be, come on, this is Linux not Windows). But I popped open synaptic and the upgrade seemed to have messed up a bit as the compiz packages were never fully pulled down, the plugins and some other stuff weren't installed. Installed them and now I'm good to go. So really, your suggestion is what did the trick, even if accidentally. Thanks!

---

### Post by PmDematagoda on 2007-12-25
There might be a problem with a Compiz configuration file, so if you removed Compiz-Fusion completely including the configuration files and reinstalled it, the problem might be solved.

---

