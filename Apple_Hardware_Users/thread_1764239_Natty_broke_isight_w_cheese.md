---
title: "Natty broke isight w/ cheese"
date: 2011-05-21
forum: Apple Hardware Users
---

### Post by goneskiing on 2011-05-21
since upgrading to Natty 11.04 my isight camera seems not working - if I run Cheese I get a big X (no device found) 

I've tried both reverting back to an older isight 1.4.2 (kola) and tried the new isight 1.6 - no luck with either with Cheese 

any suggestions ?  is there another app I should test with ?

---

### Post by catskul on 2011-05-23
I have the same problem. Have a MacBookPro 5,3. The Natty page for MBP5,3 claims that it works out of the box but only with a warm reboot from OSX first, but that doesn't even work for me.

What MB do you have? Which kernel version?

(It doesn't work with any kernel version for me and PAE kernels won't even let me boot)

---

### Post by catskul on 2011-05-23
I was able to fix my problem by installing the kernel headers package. Apparently it is needed by another package dkms which compiles new drivers for each new kernel, but for some reason is not marked as a dependency.

Upon installing the headers, dkms automatically built the relevant drivers and I was able to boot with the pae kernel, and use the isight. My PAE kernel booting problem in fact was actually an X issue because the nvidia driver failed to load because it didn exist (Because it wasn't build with dkms)

---

### Post by goneskiing on 2011-05-23
> **catskul said:**
> I was able to fix my problem by installing the kernel headers package. Apparently it is needed by another package dkms which compiles new drivers for each new kernel, but for some reason is not marked as a dependency.

Upon installing the headers, dkms automatically built the relevant drivers and I was able to boot with the pae kernel, and use the isight. My PAE kernel booting problem in fact was actually an X issue because the nvidia driver failed to load because it didn exist (Because it wasn't build with dkms)

I'll try to install the headers package - what is pae kernel ?  after installing headers, I wonder if I can simply reboot and run ift again and have isight working ?   

I am no longer running OSX on my MacBook, just Xubuntu 11.04.  Which version Mac - I'm not sure of how to get model, white dual core 13" about 2.5 yrs old.

---

### Post by goneskiing on 2011-05-24
> **goneskiing said:**
> I'll try to install the headers package - what is pae kernel ?  after installing headers, I wonder if I can simply reboot and run ift again and have isight working ?   

I am no longer running OSX on my MacBook, just Xubuntu 11.04.  Which version Mac - I'm not sure of how to get model, white dual core 13" about 2.5 yrs old.


I installed the pae kernel and headers, then rebooted, then got black screen, then adjusted down the resolution (edit|preferences) to 320x280 - it works !   Still have problem with very low volume - that will probably be fixed with a lavalier mic

---

### Post by crnixon on 2011-05-25
I've got the same problem running 11.04 on a Macbook Pro 5,5. I've tried installing the PAE kernel and headers, but no dice. I've also tried extracting the firmware from both Snow Leopard and Leopard.

---

### Post by paulinchen on 2011-05-27
Me too, driving me nuts.

Sometimes it works, but most of the time cheese doesn't detect the camera.

---

### Post by Parsa86 on 2011-06-06
This is really strange guys. I installed mint 11 and isight worked out of the box (not perfect but OK quality in cheese). Then I added mac-intel ppa and installed isight-firmware tools and it stopped working?! how can this be?!

---

### Post by barnex on 2011-07-29
Thanks! Installing the headers helped me at least one step forward. It made my camera work a few times until cheese gave up.

---

