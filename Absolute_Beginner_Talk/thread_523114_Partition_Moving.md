---
title: "Partition Moving"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-08-11
My basic ubuntu install on hda1 broke, but had a lot of my files on it. i created hda2, a swap file and hda3 the new install partition when i installed it again. I am now moving all my files from hda1 to hda3 but hit a problem. I can resize hda3 which was at the back end of the HD. I need to make it larger to accomodate the space given by the cutting of files from HDA1.

I really dont want to reinstall ubuntu again.

---

### Post by kronk on 2007-08-11
You using gparted ?

---

### Post by bobbocanfly on 2007-08-11
Yeah, gparted on the Ubuntu 7.10 ShipIt LiveCD

---

### Post by Tyke91 on 2007-08-11
7.10 isnt exactly that stable... i would suggest using 7.04 or downloading a GParted live cd iso and burning it yourself (i find this way is the best)

using a gparted cd instead of the ubuntu one seemed (at least for me) to let me extend the front and back ends of partitions

---

### Post by bobbocanfly on 2007-08-11
Ah sorry it isnt 7.10, its 7.04 Feisty LiveCD. I keep getting mixed up :(

Is there any way to do it that doesnt involve downloading and burning the gparted CD?

---

### Post by starcraft.man on 2007-08-11
> **bobbocanfly said:**
> Ah sorry it isnt 7.10, its 7.04 Feisty LiveCD. I keep getting mixed up :(

Is there any way to do it that doesnt involve downloading and burning the gparted CD?

Pop in the live CD and boot into 7.04 live CD. Then use synaptic or aptitude to install the package named "gparted". Then go into the Administration menu under System and open up gparted. There you have gparted, but remember you have to reinstall this every time its just cached to your RAM. Feel free to edit partitions now. If your not sure how to install the package, check the blue link in my sig.

As for moving this partition, be sure to back up your important data before doing this anything can always go wrong. Once done, feel free to use the move function as you like.

That's it, good luck. I prefer having my gparted CD cuz it just boots and is ready.

---

### Post by bobbocanfly on 2007-08-11
I had the Gparted on the 7.04 live cd, it just wasnt doing the right thing. I got the GParted LiveCD and its sorting everything out as i type. Thanks.

---

### Post by starcraft.man on 2007-08-11
> **bobbocanfly said:**
> I had the Gparted on the 7.04 live cd, it just wasnt doing the right thing. I got the GParted LiveCD and its sorting everything out as i type. Thanks.

Ok then, weird. I don't think theres much difference between the live CD and the custom GParted boot cd. Glad you got it sorted anyway.

---

