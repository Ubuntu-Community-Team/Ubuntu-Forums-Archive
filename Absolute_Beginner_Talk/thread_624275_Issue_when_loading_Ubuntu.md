---
title: "Issue when loading Ubuntu"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by gubemton on 2007-11-26
I have an Ubuntu 7.10 and Vista dual boot setup.

Everything is fine until I select to load Ubuntu from GRUB. I get about five error messages each going along the lines of "pci cannot allocates resource region...blah blah blah"

Then, the Splash for Ubuntu doesn't load, instead I get a black screen for about 3 minutes and then Ubuntu login shows up.

I tried google/search on the forums, but no fix. Anyone got it/have this issue?

I am using an Acer Aspire 5100

---

### Post by master_kernel on 2007-11-26
It seems like a video card error. Is your video card integrated or separate (PCI slot)?

---

### Post by gubemton on 2007-11-26
Well, it is a laptop and everytime I download/install the new drivers for it in Vista, I have to choose it under intergrated/motherboard.

The video card is an ATI xpress 1100

---

### Post by master_kernel on 2007-11-26
I don't think anything's "fatally wrong", but you should continue to look into it.

For your GRUB problem with the splash, you might try exploring your /boot/grub/menu.lst file to see if there are any weird settings.


Sorry I couldn't help more,
master_kernel

---

### Post by gubemton on 2007-11-26
Well, I found this thread. maybe someone can make sense of things for me : [http://ubuntuforums.org/showthread.php?t=265132](http://ubuntuforums.org/showthread.php?t=265132)

---

