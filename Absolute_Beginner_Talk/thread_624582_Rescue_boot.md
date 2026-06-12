---
title: "Rescue boot?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by muteXe on 2007-11-27
Hiya,
Tried to "upgrade" to gutsy the other night.  It failed dismally, something about nvdia drivers.  It also broke my feisty so i cant boot into linux at all now.
I dont really care about getting gutsy at the moment now.  My first priority is trying to get my old feisty back, with all of my old files.   I can access a menu from the boot disk so i can get to some kind of command line, but i'm not sure what to type!  I think i tried "boot: rescue" or something like that.  Sorry for the vagueness but i'm now at work and don't have my linux machine in front of me.
Can anyone help a noob please?  
Many thanks,
tom

---

### Post by Grey Box on 2007-11-27
I am sure someone else will have a better answer than me, but this is what I would do, because I think it's in the end the most time efficient if you are not sure what exactly has happened:

Get hold of a feisty install CD (or even a gutsy install CD), boot it as a LiveCD and you will be able to back up your stuff so you don't lose any of it.  With the LiveCD, you will also get a basic desktop working again so you can keep doing your work.

If you are OK with playing with the partitions on your hard drive, then you could resize your partitions and make space for a new one to install a new Gutsy/Feisty onto. I would do that, because there is always stuff I have forgotten to back up in these situations. If you install a fresh version of Ubuntu on a different partition, you can access the old one from it.

---

On the other hand, if the only problem you are having is that your display doesn't work, then you can (from your livecd, or by booting into a 'command prompt') edit the /etc/X11/xorg.conf file and change the word "nvidia" to "nv" in the display driver area. It's a line that reads:

> Driver      "nvidia"
Change "nvidia" to "nv"

--
Oh, and something I learnt to do a while back: Always have a livecd handy. Better still, install one of those very tiny Linux distributions (like Damn Small Linux or Puppy Linux) onto your computer. They take up practically no space on your hard drive but can save your bacon when something goes wrong by accident.

I hope some of that helps.

---

### Post by blop on 2007-11-27
Im not the best person to advise....but you could by nature of upgrading your current OS kind of broken Feisty...

So..

You could boot with the live cd and get access to the partition and copy stuff off to USB hard drives / flshdrives etc and reformat?

Thats what i would do...and as a general rule of thumb upgrading any OS never seems to work out as well as a fresh install.

---

### Post by jken146 on 2007-11-27
Hi,

If you can boot into Recovery Mode, typr the following to reconfigure your X settings.
```
dpkg-reconfigure xserver-xorg
```

Or as Grey Box said, you can edit xorg.conf directly.

---

### Post by muteXe on 2007-11-27
Thank you everyone :)
I have lots to try tonight when i get home!

tom

---

