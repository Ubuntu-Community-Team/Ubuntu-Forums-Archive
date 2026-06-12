---
title: "I hate x.org"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by InfamousMyzt on 2007-05-19
why, can it not realize that i have a video card and it can use it?

i always get a blue error screen saying no monitor device found, and doing a reconfigure shows its selecting my intel onboard vid card, when i need to use my ati radeon 9250, which doesnt have much support anyways.

Why am i beginning to think windows is better?

---

### Post by Titus A Duxass on 2007-05-19
Disable the on-board through BIOS.

---

### Post by hyper_ch on 2007-05-19
maybe it's not the fault of the xorg but of ati?

---

### Post by mahy on 2007-05-19
Does the Live CD boot? if yes, replace the xorg.conf on your hard drive with the Live CD's one. This is IMHO far better than dpkg-reconfigure.

---

### Post by rbil49 on 2007-05-19
Just add your intel graphics card to /etc/modprobe.d/blacklist

This will blacklist that device so the kernel won't load a module for it.

Cheers.

---

### Post by jordanmthomas on 2007-05-19
*to add to rbil49's post, here are the modules I have loaded up for my graphics:
```

i915 (yours may be i810, i945, etc
intel_agp

```
you can see what you have loaded up with the command lsmod

note that blacklilsting them and rebooting before you configure X to use your ATI card will leave you at a standard GUI-less terminal and I don't know why you'd want to blacklist your graphics card when you can just tell X to not use it.  (basically, I don't suggest the blacklisting method, but..whatever)

---

