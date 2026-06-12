---
title: "How best to edit the live CD image?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Valatar on 2007-04-20
Ubuntu is starting fairly well on the CD, except it's not installing drivers for my geforce 7900GT or my Creative X-Fi cards, leaving me at 800x600 with no sound.  Does anyone have a link to a step-by-step for adding drivers into the CD image?

---

### Post by Sklasko on 2007-04-20
Sadly, the Xi-Fi has yet to gain Linux support, the one thing that keeps me from using Ubuntu on my desktop. Unless there has been a recent update or release that I'm not aware of.

---

### Post by Terl on 2007-04-20
> **Valatar said:**
> Ubuntu is starting fairly well on the CD, except it's not installing drivers for my geforce 7900GT or my Creative X-Fi cards, leaving me at 800x600 with no sound.  Does anyone have a link to a step-by-step for adding drivers into the CD image?

You install the nVidia drivers after the install.  They are not included on the cd.

---

### Post by Spr0k3t on 2007-04-20
try this...

```
sudo apt-get install nvidia-glx-new
```

Also, the X-Fi card doesn't have a driver yet (I think... don't quote me on that), but one is due out soon.  You may need to remove the card for a while until the X-Fi drivers are released.

---

### Post by Valatar on 2007-04-20
> **Terl said:**
> You install the nVidia drivers after the install.  They are not included on the cd.

That's the thing: I want to include them on the CD.  I'm running Ubuntu as a live CD OS rather than installing it on a hard drive, so it needs the drivers on the CD if I'm to get a decent desktop resolution.

---

### Post by Terl on 2007-04-20
> **Valatar said:**
> That's the thing: I want to include them on the CD.  I'm running Ubuntu as a live CD OS rather than installing it on a hard drive, so it needs the drivers on the CD if I'm to get a decent desktop resolution.


There are other distros that have the drivers included.  I am not sure you could change the files on the Ubuntu cd without some effort.

---

