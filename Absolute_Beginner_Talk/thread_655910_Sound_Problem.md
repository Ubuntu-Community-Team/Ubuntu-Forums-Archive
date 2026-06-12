---
title: "Sound Problem"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by john wagner on 2008-01-01
Yet ANOTHER newbie question....

I'm running Dapper on a HP Pavillion Notebook (160 gig HD, 2 gig RAM) have been for 8-9 months.  Kinda slowly trying to figure things out....  My problem is thus:  I have NEVER found a driver for my sound card.  It works, sortoff, real LOW volume... edge of audible, turn off tv tell the kid to be silent, hold laptop up to ear and I can kinda hear it.  Heh.  I did a lshw -C multimedia and this is the result...

[COLOR="Red"] *-multimedia
       description: Multimedia controller
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel
       resources: iomemory:d0340000-d0343fff irq:58
[/COLOR]

Where can i find a driver that will take care of this problem?  Or is the problem elsewhere?
Thanks!

john

---

### Post by bump_ on 2008-01-01
I have an HP dv6500 laptop with an HD sound controller with Ubuntu. Out of the box I had no sound, but take a look here:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Variation B worked perfectly for me

---

### Post by john wagner on 2008-01-02
> **bump_ said:**
> I have an HP dv6500 laptop with an HD sound controller with Ubuntu. Out of the box I had no sound, but take a look here:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Variation B worked perfectly for me

Thanks!  Headed there right now, will keep you posted.

john

---

### Post by john wagner on 2008-01-02
> **bump_ said:**
> I have an HP dv6500 laptop with an HD sound controller with Ubuntu. Out of the box I had no sound, but take a look here:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Variation B worked perfectly for me

Nope.  None work for me....  I got 6.15-29-386 on my laptop.  All the fixes are for Gutsy on up.  Sigh.  Found my bug, just no fix.

Thanks anyway (I tried em all anyway...heh)

john

---

