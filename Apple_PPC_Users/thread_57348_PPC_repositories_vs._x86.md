---
title: "PPC repositories vs. x86"
date: 2005-08-16
forum: Apple PPC Users
---

### Post by Muffe on 2005-08-16
I am about to buy myself an Apple 15" PowerBook. I do have experience with Linux on x86, but not on PPC. I am relatively sure that I will run Ubuntu on it, but I wondered how many packages it was in the PPC repositories compared to x86?

Will I meet any other problems? Will all problems that compile on x86 compile on PPC?

Thanks.

---

### Post by Muffe on 2005-08-16
I'm sorry, but i posted this thread in the wrong category. Can anyone please move it to the 5.04 PPC section? Thanks.

---

### Post by ubuntu_demon on 2005-08-16
[QUOTE=Muffe]I'm sorry, but i posted this thread in the wrong category. Can anyone please move it to the 5.04 PPC section? Thanks.[/QUOTE]
 done :)

---

### Post by ssam on 2005-08-16
the ppc repos are about 99% of the x86 ones.

a few packages are windows compatability things then depend heavely on a x86 processor: wine, the windows binary codecs, ndslwrapper

there is no flash player for linux powerpc (appart from a gpl version that only plays basic flash)

there are a few programs that do not build or work on powerpc. (usually endian bugs) if you find any of these file a bug report.

there are a few powerpc only packages, mol, pbbuttons.

basically powerpc ubuntu is almost exactly the same as the x86 version (and i think more stable than the amd64 version)

---

### Post by slux on 2005-08-16
A few more things:

- There's no Java plugin for the time being and the latest JVM is IBM's build of 1.4.2.

- You won't be able to use Nvidia's or ATI's proprietary 3D accelerated drivers. DRI free software 3D acceleration is available.

- No proprietary Adobe Acrobat Reader either

- Most of the non-free games by vendors such as Linux game publishing provide only x86 binaries, same thing with ET, Americas Army etc. (it seems Q3 will be free very soon)

May have missed something. This question has been already asked in a previous thread, look that up for additional info. :)

I'd like to add that GPLFlash is currently moving forward at a better pace again and we might have a proper implementation within a year.

---

