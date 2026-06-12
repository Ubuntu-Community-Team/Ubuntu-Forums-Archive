---
title: "iMac G5 questions"
date: 2007-09-24
forum: Apple PPC Users
---

### Post by pjotre on 2007-09-24
Hi everybody!

I just recently bought a very cheap used iMac G5 1.8 Ghz / 20" Rev. A 

Right now I'm using this machine with OS X, but I'm not too happy... I'm running Ubuntu on my laptop and I get really annoyed using two different systems. 

Is anyone using the same iMac successfully with Feisty? Can I expect these things to work:

1. Standby (suspend to ram)
2. Beryl / Compiz
3. Watching DVDs

How much ram would you suggest? right now I only got 256, now I'm wondering if I need to upgrade to 2 GB or if 1 GB would be enough to run Feisty nicely.

Did install work using the regular desktop-cd (I don't haye iSight...)?

I would be happy if you could help me with this...

thanx,

pjotre

---

### Post by anemptygun on 2007-09-24
Well, one thing I can tell you is that you will definitely need to upgrade to at least 512 of RAM(A gig or 2 couldn't hurt ;) ) . I am running compiz and it eats up between 150 and 200 Mb of RAM.

---

### Post by pjotre on 2007-09-24
I'll probably get 2 gigs... It's not that expensive anymore.

So in your case compiz is working on a ppc?

---

### Post by stmiller on 2007-09-24
If your iMac has an ATI graphics card, compiz and such will most likely work. Nvidia - will not work right now, as there is no 3D nvidia PowerPC driver.

---

### Post by pjotre on 2007-09-24
Chipsatz-Modell:	GeForce FX 5200
  Typ:	Monitor
  Bus:	AGP
  Steckplatz:	AGP
  VRAM (gesamt):	64 MB
  Hersteller:	nVIDIA (0x10de)

:(

Is susend 2 ram likely to work?

---

### Post by aantn on 2007-09-24
I'm running Compiz Fusion and AWN on a rev2 imac g5 with an ati radeon 9600. I also have repository containing the latest development versions of Compiz Fusion and AWN if you're interested.

---

### Post by stmiller on 2007-09-24
Suspend will not work unfortunately, because of the Nvidia chip. The problem in a nut shell is that the machine will probably sleep just fine, but the display will not wake up, because of no hardware info from Nvidia. :(

Check out the Nouveau project, they might have a driver and more info:
[http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)

They are looking to have a good working 3D driver for Nvidia cards very soon.

---

### Post by aantn on 2007-09-24
I didn't know that suspend worked at all on Apple's ppc machines. How can I get it to work with an ati chip?

---

### Post by anemptygun on 2007-09-24
> **pjotre said:**
> I'll probably get 2 gigs... It's not that expensive anymore.

So in your case compiz is working on a ppc?

No not in my case, but I'm sure memory management works the same.

---

### Post by pjotre on 2007-09-25
thanx for your help... I guess I'll just give it try one of those days.

---

### Post by tgalati4 on 2007-09-25
A compromise is to keep Tiger on it and install XDarwin and Desktop Manager.  Desktop Manager will give you multiple desktops and in one of them you can run XDarwin and Gnome-panel which gives you a complete gnome desktop.  I do this from a remote Ubuntu machine, so I have the hardware goodness of the Mac (i.e. everything works as it is supposed to) and I can run most open source code on it as well.

You can also use Fink Commander to install many open source packages that have been natively ported to Cocoa so the graphics look nice as well.

It's not the best solution, but with Canonical dropping ppc support, I don't see fixes coming in the future.

---

### Post by aantn on 2007-09-25
> **tgalati4 said:**
> A compromise is to keep Tiger on it and install XDarwin and Desktop Manager.  Desktop Manager will give you multiple desktops and in one of them you can run XDarwin and Gnome-panel which gives you a complete gnome desktop.  I do this from a remote Ubuntu machine, so I have the hardware goodness of the Mac (i.e. everything works as it is supposed to) and I can run most open source code on it as well.

You can also use Fink Commander to install many open source packages that have been natively ported to Cocoa so the graphics look nice as well.

It's not the best solution, but with Canonical dropping ppc support, I don't see fixes coming in the future.

I don't think that Ubuntu PPC support is really that bad even if we're now officially a "community port." Besides, if you're not satisfied with Ubuntu's support, you can always go with another distribution. I hear that Gentoo has nearly a majority of PPC users.

---

### Post by anemptygun on 2007-09-25
In the end it just comes down to which distro has better support for you hardware. Use what works.

---

