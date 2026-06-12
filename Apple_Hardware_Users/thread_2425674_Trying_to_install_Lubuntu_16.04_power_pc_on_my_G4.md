---
title: "Trying to install Lubuntu 16.04 power pc on my G4"
date: 2019-08-28
forum: Apple Hardware Users
---

### Post by mickee384 on 2019-08-28
I was wondering if there is any way to install this without booting to the live cd. About 3 minutes after booting to live, the screen flickers once and the system is frozen. I have a 1.5GHZ PowerPC G4 with 2GB  RAM. I think I may not have enough RAM to go live and also install Lubuntu. Note that even the live session freezes after looking through a few applications.

---

### Post by este.el.paz on 2019-09-23
> **mickee384 said:**
> I was wondering if there is any way to install this without booting to the live cd. About 3 minutes after booting to live, the screen flickers once and the system is frozen. I have a 1.5GHZ PowerPC G4 with 2GB  RAM. I think I may not have enough RAM to go live and also install Lubuntu. Note that even the live session freezes after looking through a few applications.@mickee384:2GB RAM should be plenty of RAM, but usually these problems are relating to video card . . . did you run some boot parameters??  Or did you try any of the "nomodeset" options??  Seems like each machine has its own specific boot parameters that you need to run in the Yaboot window . . . to get the live video running . . . .  Similar to possibly needing to "configure xorg" . . . ??  Might want to search around on the interweb for your specific machine and card??

---

### Post by abtabt on 2019-09-25
hi can this help
[https://ubuntuforums.org/showthread.php?t=2090462](https://ubuntuforums.org/showthread.php?t=2090462)

---

### Post by este.el.paz on 2019-09-25
> **abtabt said:**
> hi can this help
[https://ubuntuforums.org/showthread.php?t=2090462](https://ubuntuforums.org/showthread.php?t=2090462)

@abtabt:

Thanks for posting in, seems like maybe the OP has moved along???

eep

---

### Post by mickee384 on 2020-08-16
Gave up on this, and bought a new laptop with ubuntu 20.04 installed

---

### Post by este.el.paz on 2020-08-16
> **mickee384 said:**
> Gave up on this, and bought a new laptop with ubuntu 20.04 installed

Prolly the most practical solution . . . if you don't mind sharing . . . what laptop did you buy that came with ubuntu already installed??

---

### Post by mickee384 on 2020-08-16
Mytrix LinuxBook 7350, 13.3" Full HD Slim Laptop, i5-8250U Quad-Core up to 3.40 GHz, 8GB RAM, 1TB PCIe NVMe SSD, USB-C/DP, HDMI, Backlit KB, FP Reader, Webcam, Metal Body Design, Linux 

[https://www.amazon.ca/gp/product/B088KPP4TJ/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1]("https://www.amazon.ca/gp/product/B088KPP4TJ/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1")

but I see its no longer available

---

### Post by este.el.paz on 2020-08-16
> **mickee384 said:**
> Mytrix LinuxBook 7350, 13.3" Full HD Slim Laptop, i5-8250U Quad-Core up to 3.40 GHz, 8GB RAM, 1TB PCIe NVMe SSD, USB-C/DP, HDMI, Backlit KB, FP Reader, Webcam, Metal Body Design, Linux 

[https://www.amazon.ca/gp/product/B088KPP4TJ/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1](https://www.amazon.ca/gp/product/B088KPP4TJ/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)

but I see its no longer available

@mickee384:

Thanks for the link . . . I've been looking generally at laptops that either come with linux or could easily have linux installed . . . some of them look fast, but then the price isn't "cheap" . . . but I didn't see that brand name before . . . looks pretty good . . . i5 cpu is fine for a laptop, etc . . . .

I think I want 14" or 15" . . . anyway, the saga continues, thanks for sharing that link . . . maybe it will again be "available" at some point???  : - ))

---

### Post by guiverc on 2020-08-16
> **mickee384 said:**
> Gave up on this, and bought a new laptop with ubuntu 20.04 installed

I think that was a wise decision, PPC support (not including *ppc64el*) has ended in Ubuntu, as  Ubuntu 14.04 LTS was the last main release to fully support it, and Lubuntu 16.04 LTS support (*along with other flavors that supported PPC*) ended 2019-April, being the same time  PPC support ended for main Ubuntu (ie. with 14.04 LTS).

---

