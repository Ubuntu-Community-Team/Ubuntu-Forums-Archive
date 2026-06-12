---
title: "Blender and KUbuntu not liking each other"
date: 2009-11-04
forum: Art &amp; Design
---

### Post by JevonPenguin on 2009-11-04
It seems that whenever I render, move the window, resize it, do almost anything, I get some annoying background artifacts within the blender window:

[http://http://www.majhost.com/gallery/Jevon/Bob/blenderproblems.png]("http://http//www.majhost.com/gallery/Jevon/Bob/blenderproblems.png")

It could be a problem with my graphics drivers, wanted to see if anyone else had seen this around.

Kubuntu 9.10
Blender 2.49
Gateway M-1624 standard

Thanks

---

### Post by confubar on 2010-01-02
Annoying background artifacts.... here is my screenshot, trying to run blender on Ubuntu 9.04. I see you are using 9.10... some people have advised me to upgrade from 9.04 to fix blender problems...
Please let me know if you have found any answers

---

### Post by Exodist on 2010-01-02
Blender has some issues with composting managers (like compiz). Try turning those off and see if it helps.

---

### Post by confubar on 2010-01-03
> **Exodist said:**
> Blender has some issues with composting managers (like compiz). Try turning those off and see if it helps.
Simply turning off visual effects doesnt work... I think the function may be malfunctioning.  How can I how can I make compiz compizoff????

---

### Post by Exodist on 2010-01-03
> **confubar said:**
> Simply turning off visual effects doesnt work... I think the function may be malfunctioning.  How can I how can I make compiz compizoff????
Whats your full system specs, Hard ware and software. Dont forget driver versions. I need all that to make a better assessment of what may be happening.

---

### Post by confubar on 2010-01-04
> **Exodist said:**
> Whats your full system specs, Hard ware and software. Dont forget driver versions. I need all that to make a better assessment of what may be happening.
Ubuntu 9.04 on Dell Inspiron that came with Ubuntu 
Intel&#174; Core&#153; 2 Duo Processor
Intel Graphics Media Accelerator X4500HD
Graphics card driver? good question... Hardware Drivers doesn't list anything but the wireless driver... some kind of spooky dell thing I suppose

---

### Post by Exodist on 2010-01-04
> **confubar said:**
> Ubuntu 9.04 on Dell Inspiron that came with Ubuntu 
Intel® Core™ 2 Duo Processor
Intel Graphics Media Accelerator X4500HD
Graphics card driver? good question... Hardware Drivers doesn't list anything but the wireless driver... some kind of spooky dell thing I suppose
Could be an odd bug with the Intel card/driver.
Try upgrading Blender or checking blender bug list. Other option is also upgrading to karmic.  
Some where in there it is a video/driver/program conflict type of issue. One of the 3 doesnt like the other. Upgrading to Karmic should upgrade Blender and your video driver both. Double check you do have compiz fusion complete disabled.


Cheers,
Exo

---

### Post by confubar on 2010-01-05
Is there any reason why I shouldn't use synaptic to completely remove compiz and compiz-fusion?

---

### Post by Exodist on 2010-01-05
> **confubar said:**
> Is there any reason why I shouldn't use synaptic to completely remove compiz and compiz-fusion?
Dont know, haven't tried so I am not linked in as a dependency for the gnome-desktop package Ubuntu built. I would hope so though.

---

