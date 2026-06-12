---
title: "[SOLVED] swap memory - safe to delete?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-10-26
Well, sone time ago I had Feisty, but then upgraded to Gusty (from the CD). But, now, instead of having one swap memory partition (linux headers), I have two (the one from the old deinstalled Feisty and the one from Gusty.)

Well, happens that I want to delete the Feisty one (old witch I don't need) but I don't know what it is. one of them weights 2GB in size while the other is ~500MB, that may seem logic since I had far more programs and user far more memory. But, is there a way to be SURE that the 2GB swap partition is the old one from Feisty?

---

### Post by sneezymelon on 2007-10-26
it doesn't matter which one is which.
gutsy will automatically use any swap it detects

---

### Post by Fixman on 2007-10-26
> **sneezymelon said:**
> it doesn't matter which one is which.
gutsy will automatically use any swap it detects

Can gusty use both? If no, is really an improvement to have 4 times more swap memory? (This is not a joke, I really don't know this)

---

### Post by MegaJim on 2007-10-26
depends on what you're doing - for most general operations it won't make a slight bit of difference, for playing games that require lots of ram, or video editing its possible it will make a marginal difference.

---

### Post by Niniel on 2007-10-26
I think 500 MB should be enough - I have that much on a computer with 512 MB RAM, and according to the system monitor tool, the swap file sees almost no use. But maybe if you use your computer for certain things (Maybe as a server? I have no idea.), you'll need more swap file space.

---

### Post by Fixman on 2007-10-26
Thanks a lot to ecerybody, Ubuntu has really a great commmunity

---

### Post by perce on 2007-10-26
Swap is important to be able to hibernate, because during hibernation all your ram is copied on the disk in he swap partition. If your swap is smaller than the RAM you're using, you won't be able to hibernate. This is why it is always a good idea to have as much swap as your ram.

---

### Post by Niniel on 2007-10-26
Ah, that's good to know.

What else needs a lot of swap space? GIMP?

---

