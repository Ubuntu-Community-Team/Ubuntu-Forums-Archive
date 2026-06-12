---
title: "[SOLVED] NDISwrapper &amp;amp; &amp;quot;Restricted Drivers&amp;quot; tool, what's the difference?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-11-26
**what is NDISwrapper?**

does it mean if i have a windows installation on a seperate partition, so linux makes use of the drivers from there?

---

### Post by PeterJS on 2007-11-26
NDIS is tha name of a hardware specification, or interface, or something that lots of network drivers for windows use. The NDIS wrapper is a tool to allow using windows NDIS drivers under linux. The Restircted Driver Manager is an over arching tool that covers in installation of lots of non-free drivers including the NDISwrapper, BCM43xx firmware, ATI's frglx driver, Nvidia's nvida driver, and some intel wireless cards (which is odd as I thought the driver was open source).

---

### Post by MozartlovesUbun2 on 2007-11-26
> **PeterJS said:**
> NDIS is tha name of a hardware specification, or interface, or something that lots of network drivers for windows use. The NDIS wrapper is a tool to allow using windows NDIS drivers under linux. The Restircted Driver Manager is an over arching tool that covers in installation of lots of non-free drivers including the NDISwrapper, BCM43xx firmware, ATI's frglx driver, Nvidia's nvida driver, and some intel wireless cards (which is odd as I thought the driver was open source).

so is it then different when i use restricted drivers from gutsy to enable my ATI or is it the same thing?

and how does NDIS work? does it take the dirvers from a seperate windows partition or does it downlaod them automatically?

---

### Post by MozartlovesUbun2 on 2007-11-26
**"ENVY"** also install the ATI drivers, but which one? open source or restricted? and why does envy exist, can't the ATI drivers be installed thought ubuntu enable restricted drivers?

---

### Post by PeterJS on 2007-11-26
> **MozartlovesUbun2 said:**
> so is it then different when i use restricted drivers from gutsy to enable my ATI or is it the same thing?

Using the restricted driver manage is one way to install the ATI drivers, you can also install them manually. But my experience with the nvidia drivers is that the restricted driver manager is an easier way to get it working

> 
and how does NDIS work? does it take the dirvers from a seperate windows partition or does it downlaod them automatically?
I don't know I haven't set it up in over two years, when last I used it you had to supply your own driver.

> **MozartlovesUbun2 said:**
> **"ENVY"** also install the ATI drivers, but which one? open source or restricted? and why does envy exist, can't the ATI drivers be installed thought ubuntu enable restricted drivers?

Envy (much like automatix) is a hold over from before the restricted driver manager existed to simplify the process. Why people still use envy? your guess is as good as mine. It installs the restricted driver as that's the one that's harder to get working right.

---

### Post by Hospadar on 2007-11-26
NDIS wrapper is used almost exclusively for wireless drivers.  Some wireless chipsets do not have native linux drivers, and so the windows drivers must be used to get service out of them.

NDIS wrapper has nothing to do with the restricted driver manager.  This is for hardware drivers that are released in binary formats only (i.e. are not open source) and for legal reasons these drivers cannot be included in the normal installation, and as such must be installed after the fact.  Also they are in general a little tougher to configure since the source can't be tinkered with to make them play nicer with ubuntu, hence the special tool to set them up.

NDIS wrapper - allows you to use (some, not all) windows wireless drivers)

Restricted Driver Manager - for closed source (but native to linux) drivers

---

### Post by MozartlovesUbun2 on 2007-11-26
> **Hospadar said:**
> NDIS wrapper is used almost exclusively for wireless drivers.  Some wireless chipsets do not have native linux drivers, and so the windows drivers must be used to get service out of them.

NDIS wrapper has nothing to do with the restricted driver manager.  This is for hardware drivers that are released in binary formats only (i.e. are not open source) and for legal reasons these drivers cannot be included in the normal installation, and as such must be installed after the fact.  Also they are in general a little tougher to configure since the source can't be tinkered with to make them play nicer with ubuntu, hence the special tool to set them up.

NDIS wrapper - allows you to use (some, not all) windows wireless drivers)

Restricted Driver Manager - for closed source (but native to linux) drivers

Ok but how does NDIS wrapper install these drivers? do i need windows on a seperate partion for linux to make use of it, or does NDIS work without it?

---

### Post by SparklingWater on 2007-11-26
You need to download the Windows XP version of the drivers and supply it in NDISWrapper's driver folder. It's actually quite easy. It doesn't automatically recognize drivers from the Windows partition. Wireless drivers aren't really that large anyway, so I don't see the hassle.

---

### Post by barney385 on 2007-11-26
> **Hospadar said:**
> NDIS wrapper is used almost exclusively for wireless drivers.  Some wireless chipsets do not have native linux drivers, and so the windows drivers must be used to get service out of them.

NDIS wrapper has nothing to do with the restricted driver manager.  This is for hardware drivers that are released in binary formats only (i.e. are not open source) and for legal reasons these drivers cannot be included in the normal installation, and as such must be installed after the fact.  Also they are in general a little tougher to configure since the source can't be tinkered with to make them play nicer with ubuntu, hence the special tool to set them up.

NDIS wrapper - allows you to use (some, not all) windows wireless drivers)

Restricted Driver Manager - for closed source (but native to linux) drivers

So, it's more like a generic compiler/installer?

:popcorn:

---

### Post by MozartlovesUbun2 on 2007-11-27
> **SparklingWater said:**
> You need to download the Windows XP version of the drivers and supply it in NDISWrapper's driver folder. It's actually quite easy. It doesn't automatically recognize drivers from the Windows partition. Wireless drivers aren't really that large anyway, so I don't see the hassle.

ok, so i download the normal windows drivers, so then do i need wine to run them? or does NDIS wrapper run them itself?

---

### Post by SparklingWater on 2007-11-27
NDISwrapper, in a weird way, is kind of like an emulator in itself, providing a Windows environment for drivers to run in. You do not need wine, just place them in the NDISwrapper driver folder and run NDISwrapper and you're set!

---

### Post by MozartlovesUbun2 on 2007-11-27
> **SparklingWater said:**
> NDISwrapper, in a weird way, is kind of like an emulator in itself, providing a Windows environment for drivers to run in. You do not need wine, just place them in the NDISwrapper driver folder and run NDISwrapper and you're set!

you mean i just put the downloaded .exe file in the NDIS folder and thats it?

um and where is the NDIS folder? in home?

---

### Post by MozartlovesUbun2 on 2007-11-28
question: if i enable the backports in Gutsy would it then update to the latest ATI 7.11 driver?

is that advisable?

---

