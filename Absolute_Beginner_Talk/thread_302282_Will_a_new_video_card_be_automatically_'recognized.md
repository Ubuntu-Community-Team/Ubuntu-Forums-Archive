---
title: "Will a new video card be automatically 'recognized' by Edgy?"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by wilberfan on 2006-11-18
My boss gave me an old video card of his (a PNY GeFORCE FX 5200 AGP, to be exact).

If I power off the machine, swap out the old card, and put the new card in it's place, will Edgy recognize the new card when I power back up?

Somehow, based on my experience with Ubuntu so far--that seems way too good to be true!!

I know I could probably install the card and do a RE-install of Edgy--but that wouldn't be any fun!

What's invovled in changing hardware like this, and getting it to work properly?

---

### Post by cantormath on 2006-11-18
> **wilberfan said:**
> My boss gave me an old video card of his (a PNY GeFORCE FX 5200 AGP, to be exact).

If I power off the machine, swap out the old card, and put the new card in it's place, will Edgy recognize the new card when I power back up?

Somehow, based on my experience with Ubuntu so far--that seems way too good to be true!!

I know I could probably install the card and do a RE-install of Edgy--but that wouldn't be any fun!

What's invovled in changing hardware like this, and getting it to work properly?

Just dont use ATI,
If you use Nvidia, you may need to install the drivers (I suggest using automatix2 to do this) to get full functionality from the card.  This is usually required regardless of what os you are using...

---

### Post by wilberfan on 2006-11-18
Thanks for the quick response....

The box has an nVidia emblem on it, so I'm assuming that's gonna help!  I have an nVidia card on my OTHER (AMD64x2) box, so i've had some experience using Automatix2 and adjusting the xorg.conf file to get THAT one working properly...

My question, more specifically involved whether Edgy would balk at finding a 'different' video card when I rebooted.   My sense is that so much gets 'set' during an Ubuntu install ("configuring hardware", it says at one point) that it might just hang when seeing a new piece of hardware?

---

### Post by That_Geek on 2006-11-18
no, it shouldnt, but when you install the new driver, you may reboot and get a BSOD (blue screen of death) and then you will just have to edit

```
 sudo nano /etc/X11/xorg.conf 
```

i just had to fix the vertical and horizontal refresh rate to the default that was on the side of the box that my monitor came in, and that fixed it

---

