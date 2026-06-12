---
title: "Trouble loading Ubuntu from HDD after install"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Onecat on 2007-02-11
I am on a Toshiba Laptop, Satellite M55-S139.

I installed the latest version of Ubuntu from the cd, and did it again to be sure, but I still get frozen on bootup.

I get two "PCI: Could not allocate resource region...7 & 8" or something like that breifly before the splash screen and then it goes dead and a reboot is required (ctrl-alt-del doesn't work.) 

I have tried a few boot options, I think, but it hasn't helped.

It boots and works fine from the cd, but not from the HDD. Any ideas? Thanks.

---

### Post by nickoli_02 on 2007-02-11
Try booting the recovery mode. This will give you a terminal logged in as root user. If you can get this far it's most likely a problem with xserver. What video card are you using? You will probably need to install the video drivers for your card (nvidia or ATI). If you have an ATI card, do this:

```
dpkg-reconfigure xserver-xorg
```

Now when it asks what driver to use, select "vesa" from the list, NOT ati. Do what you like for the rest of the options, and once you're done, try this

```
startx
```

This will start the xserver, and you should get a GUI. If this works then you can boot into ubuntu and then install the fglrx driver (for ATI cards). Good luck :)

---

### Post by Onecat on 2007-02-11
I cannot load recovery mode. It freezes on

hda: DMA disabled

Thre are some other ide and hda errors above it, it seems like.

---

