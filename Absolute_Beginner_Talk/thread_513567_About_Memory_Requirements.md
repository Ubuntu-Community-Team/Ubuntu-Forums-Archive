---
title: "About Memory Requirements"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by jsrealty2 on 2007-07-30
I have a friend that has a Gateway Computer that is about 5 years old & only has 128MB of SDRAM PC133 &  I have Version  6.06.1 LTS of Ubuntu on CD how much basic memory does it require to run. He is planning to put more memory in to bring it up to 512MB. He did buy some 1 stick of MICRON New 512MB PC133 133MHz DIMMs SDRAM Memory through Ebay but he put it in and it did not work. ANYBODY have any suggestions. IT would be greatly appreciated.

jsrealty2

---

### Post by Rocket2DMn on 2007-07-30
Ubuntu can run on 128, though it would be pretty slow.  He can run Xubuntu (the Xfce dektop manager) which requires fewer system resource, or he could even get a smaller distro of linux like Puppy Linux or Damn Small Linux.
If he does get more RAM, like 256 or more, he should be able to run Ubuntu fine, he just might have to pass on some of the eye candy like Compiz Fusion.

---

### Post by panther_sn on 2007-07-30
My wife tried both Xubuntu and Ubuntu on her old laptop with 64mb ram and Ubuntu works better than Xubuntu, so I would suggest your friend try Fiesty Fawn and see how they go just remember to use the alternate cd.

---

### Post by shae on 2007-07-30
When updating old computers, remember that they also often have density requirements for memory.  If the modules are too dense, they might not be recognized.  Check your motherboard's chipset for information on proper density and population methods.

---

### Post by az on 2007-07-30
> **jsrealty2 said:**
>  He did buy some 1 stick of MICRON New 512MB PC133 133MHz DIMMs SDRAM Memory through Ebay but he put it in and it did not work. ANYBODY have any suggestions. IT would be greatly appreciated.

jsrealty2

You need 256 megs to be able to run the installer from the desktop cd.

Did he put the ram in by itself on along with the other stick?

On some motherboards, you need to reset the bios configuration whenever you change your ram.  Even if the thing reaches the bios memory check, you still need to run memtest86 (from the ubuntu cd) to see if the ram timings are okay.

Other than that, the timing/density of the ram is not compatible.  If it's a density problem, you may sometimes only get your MB to see half the ram on the stick.

---

