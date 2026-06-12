---
title: "Nvidia cards and 3D acceleration question ..."
date: 2006-12-29
forum: Apple PPC Users
---

### Post by magnolia fan on 2006-12-29
Not surprisingly, I have no 3D acceleration.

When I type this into Terminal:
glxinfo | grep "direct rendering"

I receive the bad news:
"No"

Is there any way to wake up my Nvidia graphics card so I can play 3D games like 1st person shooters or am I out of luck?  I've scoured the boards and don't see anything that will help.  I even installed EasyUbuntu, but it didn't help.  I haven't touched the archives portion of EasyUbuntu since I have no idea what they do.

-thanks

---

### Post by ZERO_SHIFT on 2006-12-29
Try installing the nVIDIA drivers through Automatix[http://www.getautomatix.com/]("http://www.getautomatix.com/")

Really easy.

Good luck!

---

### Post by gamgee911 on 2007-01-02
> **ZERO_SHIFT said:**
> Try installing the nVIDIA drivers through Automatix[http://www.getautomatix.com/]("http://www.getautomatix.com/")

Really easy.

Good luck!
if you haven't already tried, this probably wont work.  I could be wrong but as far as I know, Automatix doesn't work for PPC - Sorry.  If anyone else knows how to enable NVIDIA gaphics acceleration on PPC achitecture, please post it!

---

### Post by ssam on 2007-01-03
there is no current solution. nvidia are unlikely to make a proprietary driver for powerpc.

however there is a lot of work being done on the open source [nouveau]("http://nouveau.freedesktop.org/wiki/") driver. this will have 3d acceleration, and should work on all linux architectures.

the is a pledgebank fund raiser at [http://www.pledgebank.com/nouveaudriver](http://www.pledgebank.com/nouveaudriver) if you want to donate a little money to help the nouveau project. (they are looking to get 1000 people to donate $10)

---

