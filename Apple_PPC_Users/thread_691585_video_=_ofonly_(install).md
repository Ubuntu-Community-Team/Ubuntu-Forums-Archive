---
title: "video = ofonly (install)"
date: 2008-02-08
forum: Apple PPC Users
---

### Post by NoBullets on 2008-02-08
Hi,
I'm trying to install Ubuntu in a G4 PPC Digital Audio (533MHz). I've tried both ubuntu 7.10 and xubuntu 6.06 alternate installs and I'm having several problems...
The usual (desktops/live) cds won't load, and the alternate install cd will load only with this ofonly option. The problem is that this option makes the screen to be completely out of the actual range of the monitor, I get it split in two, with a blank bar in the middle. Also, I insisted in the installation of xubuntu that way, but it keeps happening, and the system doesn't load (it gives a xfce loading error).
Is there anything I can do to fix this in the first place?

Thank you

---

### Post by stream303 on 2008-02-09
Have you tried this for the live'cd:

live-nosplash-powerpc video=ofonly

Anything in these two that might kick-start your box?

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by jdusablon on 2008-03-10
I have better luck with alternate install disks. For non-G5 new-world macs, I always use

```
install video = ofonly
```

That said, which video card are you using? Sounds like horizontal sync out of range.

I've noticed that the ppc ubuntu installs expect certain hardware and don't like upgrade/addon cards all that much.

---

