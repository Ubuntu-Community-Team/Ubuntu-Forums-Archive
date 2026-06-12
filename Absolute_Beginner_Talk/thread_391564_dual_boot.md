---
title: "dual boot"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by fluxman on 2007-03-23
Well, I bought a new laptop, with windows Vista....and while vista looks ok, and I can see that it's kind of good as an "entertainment" OS, I think it's time for me to move over to ubuntu.

I tried the live boot cd version of ubuntu and instantly loved it!!

Anywho, I use certain programs like flash professional 8, photoshop, recording software and certain other programs that I know are only on windows. I'm aware of alternatives for photoshop (pixel, gimp), but photoshop is still the daddy. Also I can't find any flash development tools on linux..let's hope adobe develops software for linux! I'm also aware of windows emulation on linux but I'm not ready to give up on windows 100% just yet.

Anywho, I don't have a vista cd, just a hidden partition on my harddrive that contains a restore version of vista. But I don't care...i have an old copy of windows2000 around somewhere which I can use (plus vista doesn't fully support many adobe products yet).

So, I'm looking to dual boot with windows2000 and ubuntu, but not really sure how to go about it? Which should I install first (and which will enable me to completely format the harddrive to get rid of the windows vista backup partition?). Also, what about communication between the 2 partitions...it's not essential, but would be nice to be able to transfer files between the 2 partitions. Also, what kind of space would you recommend for each partition. I have 80Gb harddrive and would only use windows2000 for flash development and for using photoshop, plus  a few other small programs. That's it really.

Many thanks for your help!

---

### Post by justleen on 2007-03-23
you can resize your partitions with gparted. thats enable you to free up some space for ubuntu (and if you like, leave the hidden install partition). You can simply install ubuntu on the new empty partition, GRUB will take care of the dualbooting.

Flash and photoshop (and loads of other programs) run fine on Wine. No rocket science there either in most case.
You could always run a VM machine, with windows, to run your windows apps.

as to transfering files, have a search on this forum.
You can install drivers for windows to enable etx3 support, or create a fat32 partition, both windows en linux can write to that.

---

### Post by mouseboyx on 2007-03-23
You need to install the window$2000 first and then Ubuntu, its up to you to decide how much space you need and also i think window$2000 will format the entire HD for you but I'm not sure if it doesn't then just use Gpart on the Ubuntu live cd to wipe it. As for communication between the partitions it might be possible but i don't know how to do it. You could always use WINE and ditch windows entirely (  [http://www.winehq.com](http://www.winehq.com) ).

---

### Post by Arby on 2007-03-23
To answer your question about which order to install in. Install Windows first, then Ubuntu. Windows does not play well with others and tends to make a mess of the bootloader if you install it second. Ubuntu is a lot better at detecting that you have an existing OS on the disk and setting things up accordingly. If all goes well it should also default to boot Ubuntu as first choice automatically.

---

