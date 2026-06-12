---
title: "My Wacom Pen tablet stopped working"
date: 2010-09-01
forum: Art &amp; Design
---

### Post by Kurtless on 2010-09-01
I know, I know, I had another thread where I had my tablet not working at all, but once an update came about, the tablet worked, then just today, the tablet started not working again, it was the weirdest thing. I updated my Ubuntu today with the update manager,does that have something to do with it? Can anyone tell me whats going on? What should I do?

---

### Post by Favux on 2010-09-01
Hi Kurtless,

If for example your Wacom tablet needed a compiled wacom.ko to work, say it is a Bamboo Pen tablet, then a kernel update or kernel header update will knock it out.  This is because each kernel comes with it's own modules directory and the default wacom.ko for the release, the one that didn't work, is placed in the new modules directory.  So you have to recompile a working wacom.ko and copy it over the old non-working default wacom.ko.

---

### Post by Kurtless on 2010-09-01
Ok I guess that makes sense, so what form of action should I take? What you said at the end of your last sentence? If you could, please elaborate.

---

### Post by Favux on 2010-09-01
Sure.  To recompile a new wacom.ko follow **I.** at the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  This command:
```
sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
is what copies (cp) the newly compiled wacom.ko into the new kernels modules directory.

---

### Post by BobvanderPoel on 2010-09-01
I've got a number of modules like this myself ... and each time I do an update and see a new kernel being installed I silently mutter some words I can't use on this forum.

Is there a better way to handle this? Having to manually recompile/install modules each time is getting quite old.

If this was for an exotic bit of equipment, I would see it. But the wacom tablet is pretty much "ordinary" isn't it?

---

### Post by Favux on 2010-09-01
Hi BobvanderPoel,

> But the wacom tablet is pretty much "ordinary" isn't it? 
The Bamboo Pen and Bamboo P&T's are new enough that the default Lucid wacom.ko doesn't support them.  Most of the new Bamboo series supports touch/gestures.
> Is there a better way to handle this? Having to manually recompile/install modules each time is getting quite old.
Well kernel updates are frequent after a new release but slow down after a few months.  And compiling wacom only takes about 5 minutes after you've been through it a few times.  Aren't they doing some of that with the new kernel stuff like DKMS?

---

### Post by BobvanderPoel on 2010-09-01
> **Favux said:**
> Hi BobvanderPoel,

Well kernel updates are frequent after a new release but slow down after a few months.  And compiling wacom only takes about 5 minutes after you've been through it a few times.  Aren't they doing some of that with the new kernel stuff like DKMS?

If only it were only wacom. There's also my X10 interface ...

I think that in August there were 3 kernel updates :) My memory or math might be wrong.

What is DKMS? Okay, I found this:

 [http://wiki.centos.org/HowTos/BuildingKernelModules#head-d313bd351f90d4f25a2143b7bbcff73f927731f0](http://wiki.centos.org/HowTos/BuildingKernelModules#head-d313bd351f90d4f25a2143b7bbcff73f927731f0)

Has anyone gotten this working with lucid and wacom? Would be cool if it does.

---

### Post by Kurtless on 2010-09-02
Got it working again, awesome, thanks for the info :P

---

### Post by Favux on 2010-09-04
Hi BobvanderPoel,

Looks like someone has gotten Wacom and DKMS working for Lucid.  See:  [https://launchpad.net/~ripps818/+archive/wacom](https://launchpad.net/~ripps818/+archive/wacom)

---

