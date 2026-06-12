---
title: "Blender"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by Ryan H on 2006-07-15
I downloaded and installed Blender from the repositories, but whenever I click on it to launch it from my Applications menu, it doesn't do anything. It just exits from the menu but the program doesn't launch. Any idea's why?

-Ryan

---

### Post by Perfect Storm on 2006-07-15
try launch it from your terminal/konsole:

```
blender
```

What's the output?

---

### Post by Adalgisel-Grimo on 2006-07-15
i guess you don't have a working driver for 3d-acceleration. For nvidia-cards, the build in one doesn't work with blender, so you need to install the original drivers via synaptic or from downloaded *.run or *.bin.
Make sure your driver is specified in xorg.conf. 

you will find how-to easily in this forum.

And bevor this: make a backup of your xorg.conf and have a other OS (live-CD) next to you, if anything went wrong.

happy blending!

---

### Post by Ryan H on 2006-07-16
I followed the community wiki and I got everything working! ^_^ Now Blender starts. But I have another question. Sometimes with images, or even certain when certain colors are put together pixels on my screen get discolored and often flicker, when I installed the new drivers I noticed with a few images this there weren't as many rouge pixels, but there are still some. How do I fix this?

-Ryan

---

