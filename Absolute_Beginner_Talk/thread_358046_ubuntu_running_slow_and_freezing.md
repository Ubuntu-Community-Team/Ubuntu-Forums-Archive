---
title: "ubuntu running slow and freezing"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by shadowboxer_k on 2007-02-10
hi,

i just installed ubuntu on my ibm thinkpad21 the other day. i switched from windows XP to ubuntu edgy. being a total computer dummy, i didn't pay much attention to how the disk was partitioned while installing edgy.

i was told that ubuntu should run way better on my laptop than windows xp, but it seems like it's not so much smoother. sometimes applications just freeze on me and it can't take more than two-three programs on at the same time.

i was wondering if this could have something to do with an insufficient swap size? and how could that be fixed without a reinstall?

does anyone have an idea why it is slow and freezes? 

please help. thank you.

---

### Post by BarfBag on 2007-02-10
Post more details about your laptop.  How much RAM, speed, hard drive space, etc.

---

### Post by shadowboxer_k on 2007-02-10
okay, here are the details:

CPU - 750 MHz

HD size - 20GB

RAM size - 256 MB


i really don't want to go back to windows, and i know my laptop can run ubuntu better than now. please help.

---

### Post by tedrogers on 2007-02-12
Hi,

I have an IBM T22 with a very similar spec to yours and I get these exact problems.

If I have a few apps open, and then say, open ADD/REMOVE from the Applications menu, then I experience shed-loads of disk access for ages and ages, everything slows down, the mouse gets very unresponsive and using the computer is either a case of shutting it down or waiting up to 45 minutes for it to become responsive again. This is a real pain as I'm sure you can appreciate.

I was wondering if it was a swap size issue and if this can be changed (safely) post install? Maybe with gparted? The swap is currently about 729MB.

My spec is 800Mhz, 256MB RAM and a 20GB HD (split into about two 8GB partitions as I use one for making system images for backup purposes).

Thanks.

---

### Post by tedrogers on 2007-02-13
Bump!

So should we increase the Swap size and is this even possible post install?

Thanks.

---

### Post by muguwmp67 on 2007-02-13
You don't say which desktop you are using.  If you are using ubuntu with the gnome desktop, you might try installing the xubuntu-desktop from the repositories.  I've put it on an older laptop (800 mhz) and it worked much better than gnome.

Xubuntu is based on a more streamlined window manager than ubuntu is.  It can run effectively with slower processors and less memory.

---

### Post by shadowboxer_k on 2007-02-13
hi tedrogers,

i did try to increase the swap with gparted to over 700mb, and that slowed it down so terribly that i decided to reinstall the whole thing, this time NO manual partitioning. i just installed ubuntu and let it do its thing and now it works much, much better. i can't complain.

i read somewhere that actually a big swap can slow down your machine. so maybe you should cut your swap in half and see how it goes. if in doubt, reinstall :D

---

### Post by shadowboxer_k on 2007-02-13
just to add, yes it is possible to re-partition post install with gparted. however, i don't think you should increase your swap any further, as i told you. i just checked, my swap is now 360mb and my machine isn't slow anymore.

good luck!

---

### Post by tedrogers on 2007-02-14
> **muguwmp67 said:**
> You don't say which desktop you are using.  If you are using ubuntu with the gnome desktop, you might try installing the xubuntu-desktop from the repositories.  I've put it on an older laptop (800 mhz) and it worked much better than gnome.

Xubuntu is based on a more streamlined window manager than ubuntu is.  It can run effectively with slower processors and less memory.

I'm using Gnome Edgy 6.10...I found KDE to be much more processor hungry due to the amounts of bling and eyecandy. These can of course be turned off, but I just like the simplicity of Gnome and find the non-modded KDE a bit ugly and messily organised on the whole.

Thanks for your input Shadowboxer....I appreciate this. I may try reducing my swap and will let you know if it makes any difference. I have also deleted some files off my disk, so it is less full overall, which seems to be helping a little so far.

Thanks.

---

### Post by IronMac on 2007-02-14
Thanks for this thread! I've just installed 5.1 on my T20 here (with a much faster 40-gig HD) and so far so good. I'll keep in my the swap file thingy in case things slow down significantly.

Personally, I don't find any performance differences so far between this install and the previous WinXP install.

---

### Post by tedrogers on 2007-02-14
For now my advice would be to keep your swap file size about twice the size of your RAM....this is the general rule of thumb.

---

