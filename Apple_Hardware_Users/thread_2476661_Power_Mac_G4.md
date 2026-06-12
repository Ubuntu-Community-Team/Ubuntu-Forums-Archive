---
title: "Power Mac G4"
date: 2022-07-02
forum: Apple Hardware Users
---

### Post by eduardoeltortuga2 on 2022-07-02
Hello
Can I install Ubuntu Server 22.04 LTS on a Power Mac G4?
Thanks
[IMG]https://upload.wikimedia.org/wikipedia/commons/4/41/GraphiteG4.jpg[/IMG]

---

### Post by guiverc on 2022-07-02
No.

Only the  ***ppc64el*** architecture is supported.   Your box is ***ppc*** only, where support was dropped long ago. 

Refer [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) and the ML post ([https://lists.ubuntu.com/archives/ubuntu-devel-announce/2016-December/001199.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2016-December/001199.html)) provided there.  There has been no *ppc* support for some time now  (*ppc* is not supported either thru ESM).

---

### Post by eduardoeltortuga2 on 2022-07-04
Thank you very much for helping. Have a happy 4th!

---

### Post by slickymaster on 2022-07-04
*Thread moved to **Apple Hardware Users**.*

---

### Post by kencu on 2022-09-21
You will likely be able to installed debian powerpc on this box, however, which is closely related to Ubuntu. Most users have had success. The basic text-only console interface almost always works reliably. Bringing up a full x11 graphics interface works for most people, but is somewhat dependent on the exact video card you have installed.

The single best source of information about how to proceed is here: [https://lists.debian.org/debian-powerpc/](https://lists.debian.org/debian-powerpc/)

There are various Youtube videos, walkthroughs, and other instructions, most of them quite dated, many of them with incorrect steps in them.

---

### Post by csae2608 on 2022-10-28
these computer very slow for ubuntu, installed ubuntu 10.04, for testing, but newer ubuntu, you gotta be patient.

---

