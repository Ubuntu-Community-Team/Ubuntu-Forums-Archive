---
title: "Installing a Silicon Image SATA Controller"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by highrelyguy on 2007-12-14
Hello!  I'm an engineer at Highly Reliable systems.  I'm testing the new silicon image driver for compatibility with ubuntu.  I'm not a newbie to LINUX but I've never used it in depth so there are a lot of holes in my knowledge.  

I've compiled the silicon image driver source code to produce a si3124.ko (kernal runtime loadable object).  I can do a rmmod sata_sil24 and then do a modprobe si3124 and it removes the sata_sil driver and installs the new SI3124 driver and it sees multiple drives through the port multiplier.  But my questions is, what do I do to make this module load upon boot everytime and not load the sata_sil module?

---

### Post by SgtDude on 2007-12-29
I'm heading down the same route you are.  I have a Mobo with a Sil 3132 built in, and I picked up a couple of port multipliers to throw 10 HD's on there.  My problem is that they don't seem to make a driver for anything but Redhat And Suse (and old versions at that).

Anyway, I think I have the source for the driver (pulled of Sil's website), but I've never built a kernel module before.

I have been scouring the forums on this for a couple of weeks, though, and it seems that you need to put the commands you're running to load the driver in your /etc/init folder somewhere.

I'll look around a bit and post back here when I find a solution, as this is something I'll need to get running too.

---

### Post by SgtDude on 2008-02-12
Well, I was wrong.  I didn't have the source for the driver, I had binaries precompiled for RHEL 4.

Anyhoo, it seems that if you don't mind installing an old version of CentOS, you can get this port multiplier working.  Personally, I get frustrated working with old versions, as I become accustomed to using the new tools, so I've ditched all efforts to make these things work.

I suppose Silicon Image should be commended for providing linux drivers, but also admonished for not providing drivers for contemporary distroes, or providing the source so someone else could provide drivers for contemporary distroes.

I'm holding on to these fancy little pieces of hardware, though, as support may improve in the future.

---

### Post by tekknokrat on 2008-03-14
put sata_sil in your /etc/modprobe.d/blacklist

```

blacklist sata_sil

```

this prevents module from loading.

---

