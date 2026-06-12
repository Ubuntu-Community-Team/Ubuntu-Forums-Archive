---
title: "desktop effects not working on PowerBook G4 1.67GHz"
date: 2009-03-09
forum: Apple Hardware Users
---

### Post by E-Rackattack on 2009-03-09
My PowerBook G4 1.67 GHz runs Kubuntu Hardy with KDE 4.0. I'm afraid that I've modified the system so much that I can't get desktop effects on this machine.

Can someone tell me what I need?

---

### Post by avtolle on 2009-03-09
What video card do you have in your computer?

---

### Post by mkvnmtr on 2009-03-09
I have a G4 Ibook with and I was able to get a good many desktop effects working. I don't remember what distro maybe 7.04 or later. It was so resource intensive that now tone of the first things I do is uninstall compiz. My system runs better for it. I have an ATI card and as I recall it worked out of the box as they say. I bet if you approach it with all the information of your equipment someone here will get you going.
Be sure to list your cards and what you might have done to get them going.

---

### Post by E-Rackattack on 2009-03-11
> **avtolle said:**
> What video card do you have in your computer?

I'm using an ATI Radeon Mobility 9700 series card. I had it working with Ubuntu Fiesty's Graphic effects, so it should work fine.

I'm probably missing software or something.

---

### Post by utgodmode on 2009-05-14
Guess its something to do with the software part. I have it working on G4

---

### Post by Shazz.ng on 2009-05-19
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by stream303 on 2009-05-19
On a related note - with all that is happening with ATI these days, it appears that Ubuntu has adopted a more generic video driver for ati boxes.

Ironically, this makes it easier for the majority of ATI ppc users to get to a working state, whereas before one had to manually specify the specific driver such as r128, radeon, etc along with a host of other ati-specific driver options.  This usually made it tougher for Linux beginners.

Now, the likelyhood of getting a usable system out of the box has increased, although there are still the usual suspects, such as Ubuntu's splash-screen which can still throw one for a loop right out of the gate.

If you look in /var/log/Xorg.0.log you'll be able to tell what is going on.  (That's a capital X btw..)

Unfortunately, for those that were able to have desktop affects with ati (nvidia boxes were never able to), this capability may have gone away -- for the time being..

---

### Post by monofonik on 2009-06-06
well that sucks! i was looking forward to some desktop effect magic. ****.

---

### Post by gwydionwaters on 2009-09-21
> **utgodmode said:**
> Guess its something to do with the software part. I have it working on G4

what did you do to get it working on a g4? i have a pb g4 1.25ghz and i would like to get the nvidia drivers going if i can.

---

