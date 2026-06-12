---
title: "[SOLVED] Gutsy display issues"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-10-21
Due to other issues with upgrading (which are too boring to go into!), I had to clean install Gutsy rather than upgrade.

When installed, the display was skewed to the right, so you can't, for example, see the red cross in top right hand corner.

I did some digging around, and saw references to Envy, which I had used in Feisty when trying to get Beryl to work (it never did - PC too old and graphics card too feeble - it's an NVIDIA TNT2 Riva).

So, I thought, I'll install Envy. Went through the configuration, rebooted, and....

Arrgh! Got on OK, but with a message saying:

```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first. 
```

At this stage panic set in, as this was what caused me to not be able to upgrade in the first place. And as it was only Envy that I#d since installed, I uninstalled it.

This may have been a bad idea.

Since then, I can only sign in using Recovery Mode, where I have an 800*600 screen (I know I'm getting older, but I can cope with smaller resolution!)

When I try to sign in normally, I get:

Out of scan range 63.82kHz / 60Hz

Could some kind soul put me out of my misery please? I really don't want to have to do ANOTHER clean install!

Thanks very much

---

### Post by PriceChild on 2007-10-25
*approved, moved and bumped*

---

### Post by qprfact on 2007-11-03
This solved it for me:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

---

