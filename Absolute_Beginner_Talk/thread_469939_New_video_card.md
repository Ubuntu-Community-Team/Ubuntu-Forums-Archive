---
title: "New video card"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Cheddarhead on 2007-06-10
I picked up a new graphics card, nvidia 7600gt... anywho, I have a tri-boot system, winxp, vista, ubuntu... the windows drivers were cake, but I forgot to load up ubuntu before swapping the card and uninstalling nvidia driver I had installed using automaitx for the old card... now ubuntu gui wont load, just locks up at startup... any ideas, I am a general newbie to linux

cheers

---

### Post by taurus on 2007-06-10
Boot into recovery mode form GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

### Post by w4ett on 2007-06-10
try this to get X back then you can install your new proprietary drivers:

$ sudo dpkg-reconfigure x-server-xorg

---

### Post by Cheddarhead on 2007-06-10
I used "automatix-nvidia-restore" to get my old xserver settings... worked fine...

On a side note, I set aside 10 gigs for ubuntu partition and its getting full, at bootup for ubuntu it lists the old versions so I assume they are still taking up space... how can I clean up those old ubuntu versions that hung around after updating???

Thanks!

---

### Post by w4ett on 2007-06-10
You can remove the old kernels/images via Synaptic....select the ones you don't want and delete them.  One word of advice...keep at least one previous kernel for insurance.

---

### Post by Cheddarhead on 2007-06-10
I'm thinking of wiping it altogether and doing feisty... is it a safe bet?? I see your using it, any better than edgy??

---

### Post by w4ett on 2007-06-10
I've had no problems YET.....just back-up well and take the plunge if you desire....I also advise a clean install over an update.....I've tried both and the fresh install went smoother.

---

### Post by arnieboy on 2007-06-10
> **Cheddarhead said:**
> I picked up a new graphics card, nvidia 7600gt... anywho, I have a tri-boot system, winxp, vista, ubuntu... the windows drivers were cake, but I forgot to load up ubuntu before swapping the card and uninstalling nvidia driver I had installed using automaitx for the old card... now ubuntu gui wont load, just locks up at startup... any ideas, I am a general newbie to linux

cheers

if you had used a fairly new version of Automatix (not more than 6 months old), you can run this easy command:
```
automatix-nvidia-restore
```
and restart your computer.

**EDIT**: oops.. never mind. seems like you already used the command and it worked.

---

