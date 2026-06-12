---
title: "Installed RAM question"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by BIZKeT on 2007-12-20
I have 4 gig of ram installed on my server. I know Vista Ultimate only addresses 3 gig, but Ubuntu 7.10 is only showing 3 gig as well. Is this a hard cap? The mother board (asus a8n-sli-deluxe) will support 4 gig, and on POST it is showing 4 gig.

Thanks in advance for any help you guys can provide.

BIZKeT

---

### Post by SOULRiDER on 2007-12-20
I believe you need to run a 64 bit version or recompile the kernel to add big memory support.

---

### Post by eldragon on 2007-12-20
since your video card's ram is mapped to main memory too, having 4gig of ram, + video ram ends up being more than 4gb of ram, thus you need a 64bit OS and your bios set correctly.

if you already have a 64bit os, check for bios settings concerning more than 4gb of ram...

---

### Post by ukripper on 2007-12-20
You NEED 64Bit Version of Ubuntu

---

### Post by LaRoza on 2007-12-20
> **BIZKeT said:**
> I have 4 gig of ram installed on my server. I know Vista Ultimate only addresses 3 gig, but Ubuntu 7.10 is only showing 3 gig as well. Is this a hard cap? The mother board (asus a8n-sli-deluxe) will support 4 gig, and on POST it is showing 4 gig.

Thanks in advance for any help you guys can provide.

BIZKeT

The motherboard supports it, the OS doesn't. To use 4 GB of RAM you need a 64 bit OS. Since you already have the RAM, I suggest you get the 64 bit Ubuntu.

---

### Post by BIZKeT on 2007-12-20
Does the 64bit version of Ubuntu install the 32bit libs? I am a gamer for the most part and will be running Cedega which does not have native 64bit support.

---

### Post by ukripper on 2007-12-21
> **BIZKeT said:**
> Does the 64bit version of Ubuntu install the 32bit libs? I am a gamer for the most part and will be running Cedega which does not have native 64bit support.

No, you would need 64bit libs only on 64bit.

---

### Post by BIZKeT on 2007-12-21
> **ukripper said:**
> No, you would need 64bit libs only on 64bit.

I understand  that. Does the 64bit version install the 32bit libs as well as the 64bit libs so that I can run 32bit only apps?

---

### Post by shae on 2007-12-21
Yes you can install 32bit libs so you can run 32 bit applications in 64bit ubuntu.

---

### Post by BIZKeT on 2007-12-22
> **shae said:**
> Yes you can install 32bit libs so you can run 32 bit applications in 64bit ubuntu.

I know I -can-, I am wondering if it does so during install.

---

