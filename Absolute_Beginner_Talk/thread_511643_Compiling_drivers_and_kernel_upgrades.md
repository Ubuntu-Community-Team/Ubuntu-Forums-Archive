---
title: "Compiling drivers and kernel upgrades"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by DaveAK on 2007-07-28
If I compile a driver using a specific kernel, and then later upgrade to a newer kernel, do I have to recompile the driver?

The reason I ask is that there's a driver for a 3M touch screen I need to compile, but it's not for the latest kernel.  It doesn't look like they keep their drivers as current as the kernel updates.  I need to know so that I don't upgrade and break my driver.  The current driver won't compile under Fiesty.

---

### Post by DBStevens on 2007-07-28
You should redo the drivers since things may have changed in the kernel that the drivers need to know.

It is also possible that the driver even if recompiled may no longer work.  Drivers that reside outside of the kernel (and some that are inside) have to be handled by you or others seperate from the kernel.

---

### Post by LeonardoDV on 2007-07-28
> **DaveAK said:**
> If I compile a driver using a specific kernel, and then later upgrade to a newer kernel, do I have to recompile the driver?

The reason I ask is that there's a driver for a 3M touch screen I need to compile, but it's not for the latest kernel.  It doesn't look like they keep their drivers as current as the kernel updates.  I need to know so that I don't upgrade and break my driver.  The current driver won't compile under Fiesty.
DaveAK,

did you copile the driver for 3M Touch Screen? I have lot of problems trying to copile it.

Any suggestion?

LeonardoDV

---

### Post by DaveAK on 2007-07-28
> **LeonardoDV said:**
> DaveAK,

did you copile the driver for 3M Touch Screen? I have lot of problems trying to copile it.

Any suggestion?

LeonardoDV
No, I haven't got it to compile yet, and my fear is that if I do go back to an earlier kernel/distro and get it to compile, then I'll no longer be able to do any upgrades.  That's why I posted this thread, to confirm my fear.  But anyway, I'm going to load an old copy of MEPIS that I have and see if I can get it to compile for that distro.  It may be a few days until I get around to it, but I'll post my result here for you.

---

### Post by DaveAK on 2007-07-28
> **DBStevens said:**
> You should redo the drivers since things may have changed in the kernel that the drivers need to know.

It is also possible that the driver even if recompiled may no longer work.  Drivers that reside outside of the kernel (and some that are inside) have to be handled by you or others seperate from the kernel.
Thanks for your reply, but this doesn't sound too hopeful for my situation with this particular driver. :(  The one saving grace is that it will be on a single app machine, so if I can get it working I won't really need to do any upgrades, (hopefully!).

---

### Post by az on 2007-07-28
If you compile a module for a version of the kernel, it won't be binary-compatible with a different version of the kernel.  You will have to recompile that module.

Fortunately, if a driver is free-libre software (not licenced under a proprietary license), works well and has a community supporting it, it can get integrated into the upstream source of the kernel.  Then the module gets shipped with the kernel and you no longer need to compile it yourself.

If the driver is not free (proprietary), then you are screwed.  It will never become part of the kernel.  Your only hope is that the driver is redistributable and it may get included into the linux-restricted-modules package.  If this is the case, file a bug report to ask for it to be supported.

---

### Post by DaveAK on 2007-07-28
> **az said:**
> If you compile a module for a version of the kernel, it won't be binary-compatible with a different version of the kernel.  You will have to recompile that module.

Fortunately, if a driver is free-libre software (not licenced under a proprietary license), works well and has a community supporting it, it can get integrated into the upstream source of the kernel.  Then the module gets shipped with the kernel and you no longer need to compile it yourself.

If the driver is not free (proprietary), then you are screwed.  It will never become part of the kernel.  Your only hope is that the driver is redistributable and it may get included into the linux-restricted-modules package.  If this is the case, file a bug report to ask for it to be supported.
Sounds like I'm screwed then.  Their web page says it's compatible with all 2.4 and 2.6 kernels, but I think that's out of date, it doesn't work with the later 2.6 kernels.  Hopefully they'll get around to releasing an update soon.  In the meantime I'm going to install MEPIS on that particular machine and see if it will compile for an earlier kernel.

---

