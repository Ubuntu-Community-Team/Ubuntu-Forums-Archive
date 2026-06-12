---
title: "Can't Reduce Screen Brightness on 3.1 MBP"
date: 2009-04-11
forum: Apple Hardware Users
---

### Post by bigdawg737 on 2009-04-11
Does anyone know how to reduce the screen brightness in Intrepid?  I've tried installing pommed and no such luck.  I can't reduce or increase the brightness on my screen.  Any help is appreciated.

---

### Post by cyberdork33 on 2009-04-11
Have you followed direction here:
[https://help.ubuntu.com/community/MacBookPro3-1/Intrepid](https://help.ubuntu.com/community/MacBookPro3-1/Intrepid)

---

### Post by bigdawg737 on 2009-04-12
Tried this previously with no luck.  The keys to adjust screen brightness (F1 & F2) do not work at all.  The keys to adjust the keyboard brightness bring up graphics on the screen as if they are working, but do nothing.

---

### Post by cyberdork33 on 2009-04-13
well, just to get you started in the right direction,

you need to uninstall pommed as it is not needed and conflicts with the newer fixed packages in the mactel ppa.

You should also uninstall mouseemu as it can cause weird issues with the keyboard as well.

---

### Post by JGreenidge on 2009-04-13
> **cyberdork33 said:**
> well, just to get you started in the right direction,

you need to uninstall pommed as it is not needed and conflicts with the newer fixed packages in the mactel ppa.

You should also uninstall mouseemu as it can cause weird issues with the keyboard as well.

I'll take a crack at this if I knew how. How, Ubuntu mavens?

Jim

---

### Post by Peasantoid on 2009-04-13
```
sudo apt-get remove pommed
sudo apt-get remove mouseemu
```
Is that what you were asking...?

---

### Post by JGreenidge on 2009-04-13
> **Peasantoid said:**
> ```
sudo apt-get remove pommed
sudo apt-get remove mouseemu
```
Is that what you were asking...?

Thanks for the swift response!!

Just to be sure -- this _might_ remedy the brightness keys issue on a PPC G3 iBook, yes? If it doesn't work, can these two programs be reinstated as before? Also -- maybe related or a different topic, can't Ubuntu spin down the HD or reduce processor speeds automatically like OS-X? Ubuntu seems to drive the HD constantly till the excessive heat kicks the fan on -- something that hardly occurs even during summer here in NYC under OS-X. Or is that a pending fix if Ubuntu engineers are even aware of it?

Thanks!

Jim

---

### Post by cyberdork33 on 2009-04-13
> **JGreenidge said:**
>  Just to be sure -- this _might_ remedy the brightness keys issue on a PPC G3 iBook, yes? 
This thread is about the brightness keys on an Intel-Based MacbookPro3,1. It will likely not help you with a PowerPC machine.


There are SEVERAL differences between the PPC and Intel architectures. I would suggest you open a different thread and ignore what you see here.

---

