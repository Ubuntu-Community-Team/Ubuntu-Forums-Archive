---
title: "Xubuntu Live CD Not Loading"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Pobega on 2006-12-30
I'm trying to get Xubuntu Live working on my sister's laptop, but it doesn't seem to want to load into Xfce. It's a Dell Inspiron 1200, with:

Intel Celeron Processor 1.40 GHz
248 MB RAM
Phoenix ROM BIOS Plus
Mobile Intel 915 GM/GMS 64 MB Video card

If you need anything else I'd be happy to get the information, but I figure those are the main things that would be causing any trouble. Thanks for your help.

---

### Post by taurus on 2006-12-30
You mean it would boot but X can't start!  If that's the case, you can use the alternate CD to install it on her laptop then.

---

### Post by Pobega on 2006-12-30
Well if it won't boot X then wouldn't it give me problems with X after I install it as well?

---

### Post by taurus on 2006-12-30
Not necessary...  And even if it does, you can configure it again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Pobega on 2006-12-30
Alright, I'm downloading the LiveCD and I'm going to be burning it onto a DVD. Thanks for your help! I'll definitley have more questions soon concerning her Network Card, so I'll be back :D

---

### Post by taurus on 2006-12-30
Are you downloading the LiveCD or the DVD?  Didn't you already have the LiveCD and you can't get X to run on your laptop?  No need to go for the DVD version since it would take much longer to download than the alternate version.

---

### Post by Pobega on 2006-12-30
No no, I'm putting Xubuntu Alternate CD on a DVD since I've run out of CDs. But Xfburn doesn't seem to like DVDs, any suggestions?

---

### Post by taurus on 2006-12-30
You can use k3b to burn it from Linux!

---

### Post by Tazix on 2006-12-31
> **Pobega said:**
> I'm trying to get Xubuntu Live working on my sister's laptop, but it doesn't seem to want to load into Xfce. It's a Dell Inspiron 1200

I can't comment on your DVD burning problems mainly because I haven't tried to burn a DVD in Xubuntu.

However...  Booting **ANY** linux CD or DVD may require additional boot parameters, depending on the hardware you are trying to install it on.

Example:
**linux pci=noacpi noapic**

Typed in at the very beginning of the boot process. (Hit ESC when the first xubuntu menu comes up)

Though the Dell Inspiron 1200 isn't listed here... this should give you an idea of what I'm talking about.

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell?highlight=%28noapic%29](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell?highlight=%28noapic%29)

If noacpi and noapic boot switch commands doesn't solve your live cd problem... you may need another switch that forces "framebuffer graphics mode"... but I don't remember the switch command off the top of my head.  Usually noacpi and noapic solve most linux hardware incompatibility issues for install.

Hope that helps,

-Taz

**EDIT:** After booting my live CD and hitting F1 for help options... you probably want to try:

live noapic nolapic

typed in at the "boot:" prompt, which will look like:

**boot: live noapic nolapic**

If you still can't boot the live CD through to desktop... add pci=noacpi at the beginning, which will look like:

**boot: live pci=noacpi noapic nolapic**

---

### Post by Pobega on 2006-12-31
Thanks for your help, but I just installed with the alternative install disc and her system is working great :D With the exception of the wireless card, we're still fiddling with that.

---

