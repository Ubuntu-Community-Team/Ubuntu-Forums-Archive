---
title: "Blank Screen with only a curser"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Ameraturk on 2007-09-08
Hello,
I am very new to this but loving learning all the new information.

Problem: Blank Screen with only a curser after Ubuntu Studio 7.04 has loaded.
My computer (old) Intel Celeron 1400 mhz, 1.4 ghz, 256 RAM.  Graphics (I think)Intell chipset 810e
I will provide any information but may need help finding it.  

Thanks for the help

---

### Post by p_quarles on 2007-09-08
I doubt you'll have much success getting Ubuntu Studio working on that machine. Gnome is already pushing its limits, and a low-latency kernel on top of that -- I'm not surprised it won't load X.

That said, you can try this:
```
sudo lshw | less
```
Look at the output to find your video card. If it's *not* an Intel chipset, you might be able to get it running (very slowly, though) with the correct graphics driver. If it is Intel, it already has the correct driver, and that's not the problem.

My suggestion is that you try downloading and installing Xubuntu. It's a lighter weight version that will work much better on that machine.

---

### Post by diatribe on 2007-09-08
indeed, 256mb of ram is rather low for what you are trying to do, try either xubuntu or adding more ram

---

### Post by vincentvee on 2007-09-08
definately try xubuntu
it is a lot lighter than the others......and good luck with it
you can get xubuntu [here]("http://www.xubuntu.org/get#feisty")
also... i had ubuntu running on a laptop with similar specs to what you have listed, i had to install from version 5.10 and then do step upgrades all the way to 7.04, however 7.04 was a drain on the old thing, much better after i stuck in another 256 of ram, but it did run on 256 initially, but it would not install from the disk, only from upgrade, which i thought was strange

---

### Post by Ameraturk on 2007-09-09
Thanks for your help. I will try X instead of Studio:(.  

Have a great day

---

