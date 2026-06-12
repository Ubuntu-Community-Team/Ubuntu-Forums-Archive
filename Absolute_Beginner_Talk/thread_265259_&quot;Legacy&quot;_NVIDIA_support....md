---
title: "&quot;Legacy&quot; NVIDIA support..."
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by jamesivie on 2006-09-25
I finally got Ubuntu Dapper running on a slightly older system of mine, on which I previously had Fedora Core 3 running just fine.  After an apparently successful installation, the system would hang right about the time the GUI was supposed to come up.  As a result, I immediately suspected the video drivers.  It took me about 5 hours of googling to find out how to solve the problem.  My question is, why doesn't Ubuntu either automatically detect that this card isn't supported and just tell me so instead of trying to use the wrong driver and hanging, or automatically install the correct driver?

---

### Post by whizbaby on 2006-09-25
> **jamesivie said:**
> My question is, why doesn't Ubuntu either automatically detect that this card isn't supported and just tell me so instead of trying to use the wrong driver and hanging, or automatically install the correct driver?
To understand this you need a little knowledge about the package repositories:
some contain entirely free software, some (licence) restricted software and some non-free software. Ubuntu default is only to come with entirely free software (to avoid lawyer trouble). So ubuntu tries to run your card with the free nv driver (which doesn't seem to work, don't know why). nvidia-glx-legacy is a restricted package.

---

### Post by jamesivie on 2006-09-27
OK.  Actually, I found out that this isn't as common a problem as I thought it was.  I had a second (PCI) video card installed (a GeForce 2--the AGP one is a TNT2).  Dapper gets confused and doesn't use either one correctly.  When I removed the PCI video card, the Live version started working and a full reinstall from that point worked first try.  Hopefully anyone else in the same situation will find this post and be able to get up and running right away.  I'll put the PCI card back in once I'm fully up and running and see if I can get it to work too.

---

### Post by jamesivie on 2006-09-27
> **whizbaby said:**
> To understand this you need a little knowledge about the package repositories:
some contain entirely free software, some (licence) restricted software and some non-free software. Ubuntu default is only to come with entirely free software (to avoid lawyer trouble). So ubuntu tries to run your card with the free nv driver (which doesn't seem to work, don't know why). nvidia-glx-legacy is a restricted package.

Thanks for your response.  That makes sense, but it would be nice if it said that was the problem instead of just hanging.

---

