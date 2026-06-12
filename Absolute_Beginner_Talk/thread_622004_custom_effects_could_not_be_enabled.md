---
title: "custom effects could not be enabled"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Willye on 2007-11-24
i have ubuntu 7.10 running under VMware, i have a mother board intel, and the graphics card is printed in it, i mean i don't have other graphic card device, is possible to enable visual effects ?

---

### Post by qamelian on 2007-11-24
> **Willye said:**
> i have ubuntu 7.10 running under VMware, i have a mother board intel, and the graphics card is printed in it, i mean i don't have other graphic card device, is possible to enable visual effects ?

Since you are running under VMware, you won't be able to enable Desktop Effects, because currently VMware (nor any other VM solution I'm aware of) cannot support 3D acceleration needed for the effects.

---

### Post by Willye on 2007-11-24
ok, if i install a graphics card it would work well?

---

### Post by qamelian on 2007-11-24
> **Willye said:**
> ok, if i install a graphics card it would work well?
No. As long as you are running Ubuntu under VMware instead of actually installing directly on the PC, Desktop effects will not work, at least not until VMware is able to directly access the video hardware. They are working on solving this but I don't know how long it may take. It makes know difference which video card you have.

---

### Post by sailor2001 on 2007-11-24
graphics cards= $100-$500

---

### Post by Willye on 2007-11-24
ok, thanks a lot, maybe i'll install ubuntu as my primary OS

---

### Post by qamelian on 2007-11-24
> **Willye said:**
> ok, thanks a lot, maybe i'll install ubuntu as my primary OS
No need to go that far, if you're still in the process of evaluating it for your needs, YOu always have the option of setting your PC up to dual-boot with both Windows and Ubuntu as options. That way you still have a fall-back if necessary.

---

### Post by shamasis on 2007-11-24
Softwares like VMWare produce a "virtual hardware set" to the guest OS that is installed under it. In your case it is UBUNTU running under Windows. This limits the actual capabilities of your computer that UBUNTU (or any otherOS installed under VMWare-like softwares) can use.

I have acquaintances, who are running Ubuntu directly installed on their hard drive (i.e. it does not need VMWare or Windows to run,) and they can use almost all desktop effects. They have similar Intel on-board graphics of pre-historic age and everything seems to work just fine.

**Solution for you:**
[LIST]
[*]Install UBUNTU as an OS directly onto your hard-disk (dual-boot with windows)
[/LIST]

---

### Post by shamasis on 2007-11-24
> **Willye said:**
> ok, thanks a lot, maybe i'll install ubuntu as my primary OS

You said this perhaps because you do not have free space in your hard drive. Don't worry, if you have space to run Ubuntu on VMWare, uninstalling all of those will give you enough space to run the actual OS!!! LOLZ :P

You can resize one of your windows drive partitions to give you space to install the OS

---

