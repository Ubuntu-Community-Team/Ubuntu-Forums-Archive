---
title: "How can you run Wine in PPC Ubuntu?"
date: 2007-05-02
forum: Apple PPC Users
---

### Post by prince_alfie on 2007-05-02
I would like a step-by-step direction to install Wine on my G4 iBook. That would be great if I could get some help in this regard. Thanks!

I would like to run some Windows programs.

---

### Post by jwbaker on 2007-05-02
You can't.  Next question.

---

### Post by prince_alfie on 2007-05-02
So no way to emulate Windows programs in Ubuntu?

---

### Post by Auria on 2007-05-02
> **prince_alfie said:**
> So no way to emulate Windows programs in Ubuntu?

In Ubuntu yes, on PPC no.  Windows programs are not designed for PPC architectures, nor is wine.

---

### Post by calum on 2007-05-02
You could try running qemu or bochs on PPC, but they can be tricky to configure run quite slowly (since all the x86 emulation has to be done in software).

---

### Post by Gen2ly on 2007-05-02
I've heard of it being done but you'd take such a hit it really wouldn't be worth the time likely.

---

### Post by stmiller on 2007-05-03
qemu can emulate x86 code on ppc. But it is very slow, esp on G4 machines. And very buggy...

---

### Post by KonstantinosX on 2007-05-04
> **Auria said:**
> In Ubuntu yes, on PPC no.  Windows programs are not designed for PPC architectures, nor is wine.
Agree. Still "Virtual PC"  on PPC seems to do the job fine.. on my G5 iMac it emulates a 900Ghz PC with 256 RAM.. Slow but works fine...

---

### Post by rikai on 2007-05-04
> **KonstantinosX said:**
> Agree. Still "Virtual PC"  on PPC seems to do the job fine.. on my G5 iMac it emulates a 900Ghz PC with 256 RAM.. Slow but works fine...

I believe you mean 900mhz, not ghz. :lolflag:

---

### Post by stmiller on 2007-05-04
> **rikai said:**
> I believe you mean 900mhz, not ghz. :lolflag:

It's a special version of the iMac, altered by a team from MIT and NASA.

---

### Post by mlabossi on 2007-05-05
There is a project called [Darwine]("http://darwine.opendarwin.org/") that is aimed at porting WINE to the Mac. Of course, with the switch to Intel chips, the need for this is not as great. Except, of course, for those who have the older (G4, G3) Macs.

For running Windows on pre-Intel macs, the best option (taking into account speed, ease of use, compatibility) is Microsoft Virtual PC. This product has been discontinued. There is a Windows version that is a free download.

---

### Post by Auria on 2007-05-05
> **mlabossi said:**
> There is a project called [Darwine]("http://darwine.opendarwin.org/") that is aimed at porting WINE to the Mac. Of course, with the switch to Intel chips, the need for this is not as great. Except, of course, for those who have the older (G4, G3) Macs.

For running Windows on pre-Intel macs, the best option (taking into account speed, ease of use, compatibility) is Microsoft Virtual PC. This product has been discontinued. There is a Windows version that is a free download.

AFAIK Darwine is pretty much dead

---

