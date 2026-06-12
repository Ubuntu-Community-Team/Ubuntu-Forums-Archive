---
title: "Flightgear runs VERY slow in Gutsy"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by wheelhorse2347 on 2007-12-08
I just did a fresh install of Gutsy this past week.  Everything seems to be working fine, however Flightgear is barely running.  I would guess it's running about 1fps.  When I run glxgears It is showing about 850fps.  I think I have 3D rendering enabled, however I'm not sure.  It seemed to run fine on Edgy.

Specs.

AMD 64 Processor
Nvidia Nforce card
512 MB ram
80GB hard drive

If you have any ideas, let me know

Thanks!

---

### Post by taurus on 2007-12-08
Are you sure you have installed nVidia driver for your graphic card?  What does it say when you click System -> Administration -> Restricted Drivers Manager?

---

### Post by Vadi on 2007-12-08
My glxgears shows 1200fps, and flightgear doesn't run at all. It's very resource-intensive.

To check if you have direct rendering enabled, you can do

glxinfo | grep rendering

(to explain - glxinfo will give you a whole lot of messages about your graphics. Doing | grep  rendering will filter them by lines only containing word "rendering").

---

### Post by wheelhorse2347 on 2007-12-08
To Taurus, it says that I have the latest driver.

"NVIDIA Accelerated Graphics Driver (Latest Cards)

To Vadi, it says that I do have direct rendering enabled.  

I wonder if I have the driver for my graphics card enabled.  I have a 'S3 ProSavage8' card.

---

### Post by Vadi on 2007-12-08
I think your card is just really old (just as mine).

So it's simply a hardware limitation.

---

### Post by wheelhorse2347 on 2007-12-08
That's always a possibility.  The only thing that's driving me crazy is that it was running perfectly well on Edgy Eft (My last install).  It doesn't look like I'm finding any drivers made for linux for this graphics card.

---

### Post by wheelhorse2347 on 2007-12-08
I don't quite know what it did, but I went into 
gksudo gedit /etc/X11/xorg.conf

and changed the graphics card value to 16 and flightgear seems to work.

---

### Post by taurus on 2007-12-08
> **wheelhorse2347 said:**
> To Taurus, it says that I have the latest driver.

"NVIDIA Accelerated Graphics Driver (Latest Cards)

To Vadi, it says that I do have direct rendering enabled.  

I wonder if I have the driver for my graphics card enabled.  I have a 'S3 ProSavage8' card.

Do you have S3 ProSavage8 card or nVidia card?

---

