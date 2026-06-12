---
title: "Does Live Running OK Mean Install Will be OK?"
date: 2005-06-17
forum: Absolute Beginner Talk
---

### Post by polo_step on 2005-06-17
I've had a lot of painful experinces with trying to install other distros in the past.

The Live versions of Ubuntu & Kubuntu "install" fine with no system or operational problems on my machine.

Does this mean that the true hard installation CD will do a clean installation and work properly?

I always assumed that this was the purpose of the Live CD - to do a safe test of how the distro was going to work prior to doing something really irrevocable, but I suppose that there's no reason to assume that; they could be totally different.

Thanks for any clarification!

---

### Post by tread on 2005-06-17
Yes, the live cd is setup the way your real setup would be. So if you have no issues with the live cd, the installation should go fine too :)

---

### Post by Xian on 2005-06-17
The best thing about a LiveCD is that you get a feel for the extent to which your hardware is supported and other functionality issues. However, it does not in any way guarantee that you will encounter no problems during the installation, as for example there is not a partitioning step on the LiveCD.

I would advise that you perhaps elaborate on what some of your previous issues were with Linux installs, and then we might be able to recognize them or have an increased assurance that they will not be repeated the next time.

---

### Post by polo_step on 2005-06-17
[QUOTE=Xian] However, it does not in any way guarantee that you will encounter no problems during the installation, as for example there is not a partitioning step on the LiveCD.

I would advise that you perhaps elaborate on what some of your previous issues were with Linux installs, and then we might be able to recognize them or have an increased assurance that they will not be repeated the next time.[/QUOTE]
As far as partitioning, I will be doing this over an existing OEM Linspire (also Debian based) installation on a new box, so I'm assuming that it will just use the existing partitions and blow Linspire off, installing over it.

The other distros that didn't work primarily didn't work because of bugs in the installations software (my favorite was Mandrake, which prompted you to make selections that didn't exist on the interface!), or some problems configuring hardware on computers I no longer have.

---

### Post by verbalshadow on 2005-06-18
[QUOTE=polo_step]I've had a lot of painful experinces with trying to install other distros in the past.

The Live versions of Ubuntu & Kubuntu "install" fine with no system or operational problems on my machine.

Does this mean that the true hard installation CD will do a clean installation and work properly?

I always assumed that this was the purpose of the Live CD - to do a safe test of how the distro was going to work prior to doing something really irrevocable, but I suppose that there's no reason to assume that; they could be totally different.

Thanks for any clarification![/QUOTE]
 actually i have had more trouble with the livecd then the install.
ie to get the livecd to work i had to use --nolapic --noapic 
with the install cd i had no problems at all.

---

### Post by polo_step on 2005-06-18
[QUOTE=verbalshadow]actually i have had more trouble with the livecd then the install.[/QUOTE]
After having Kubuntu Live work fine for me, it started having problems after KDE desktop was almost loaded.  I'd get:

"Process for media protocol died unexpectedly"

...and a similar error for something to do with the filesystem.

I bit the bullet and went ahead and loaded the Install version anyway, and it seems to be OK, aside from some monitor configuration limitations that scare me (only available refresh rate is too hot, I think) and Konqueror's propensity for crashing, crashing, crashing.

Nothing "dying unexpectedly" except Konqueror on some sites, though.

---

