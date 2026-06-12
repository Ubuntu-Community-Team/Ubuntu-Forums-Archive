---
title: "nVidia drivers causing slowdown"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Sabretooth on 2007-09-03
OK, system specs first:

Pentium III 1.0 GHz
nVidia GeForce FX 5200 w/ 128 MB VRAM
512 MB RAM
10 GB Hard Drive (Ubuntu Feisty)/80 GB Windows XP Dual Boot.

I've always found my Ubuntu to be considerably slow, but I blamed it on GNOME. Some days ago, I reinstalled it and it ran extremely fast (which it should!) I decided to trace back slowly how it could go slow and I realized that once I installed the nVidia drivers (using the Restricted Drivers manager), things instantly became slow. I've also found Firefox graphics glitches, which I'll elaborate if anyone wants to. I've also tried ENVY, but it gave the same effect (after disabling the restricted drivers, of course). I've heard of Nouveau, though I hear it's still in development. :(

I really want to use Compiz Fusion, but it seemingly doesn't work without the drivers. Is there any way I can get it working without nvidia's drivers, or get any substitute drivers?

---

### Post by Kobalt on 2007-09-03
Ok, first : you don't want to try Nouveau that soon. It's very early in development.
Using the restricted drivers manager to install your nVidia drivers can sometimes produce weird effects. Try to search in Synaptic first if you have the nvidia-glx or nvidia-glx-new package installed. Your card seem new enough to use nvidia-glx-new so if you have the "old" drivers instead of the new, this could be a reason...

---

### Post by Sabretooth on 2007-09-03
Yep, nvidia-glx-new is installed. :( Any other suggestions?

---

### Post by Kobalt on 2007-09-03
Have you tried using htop to see what is actually causing the slowdowns ?

---

### Post by Sabretooth on 2007-09-03
The CPU and MEM reserves are far from full, so I can't exactly detect anything that would cause a slowdown. Still, let me clarify. I'm not exactly slow, but more like sluggish. Redrawing takes a while, buttons are a little slow etc.

---

