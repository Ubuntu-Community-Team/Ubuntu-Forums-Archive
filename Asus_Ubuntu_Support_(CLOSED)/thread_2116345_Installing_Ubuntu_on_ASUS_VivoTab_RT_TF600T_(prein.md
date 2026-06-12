---
title: "Installing Ubuntu on ASUS VivoTab RT TF600T (preinstalled Windows RT)"
date: 2013-02-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Denis63 on 2013-02-15
Hi everyone!

I have an ARM based tablet (ASUS VivoTab RT on Tegra 3) with preinstalled Windows RT. But I'm going to install Ubuntu 12.10 for ARM (armhf+omap4.iso) on my tablet! Sad, but my tablet has an UEFI & Secure Boot, that complicate the installation process :mad: At the same time, [is wrote]("http://askubuntu.com/questions/206950/12-10-uefi-secure-boot-install"), that Ubuntu 12.10 supports Secure Boot & UEFI by default! Does it mean, that bootable flash-card within Ubuntu 12.10 distributive for ARM, created in Ubuntu 12.10 (installed on my PC), may be used to install ARM-Ubuntu on my tablet? Otherwise Canonical bootloader (with secure boot & UEFI support) is allowed to be used with x86 machines only???

---

### Post by vitj on 2013-02-24
I am also looking to do this but can't find any information specific to this tablet.

Have you tried it yet with any results? Apparently secure boot cannot be disabled on this device

> 

Mandatory. Enable/Disable Secure Boot. On non-ARM  systems, it is required to implement the ability to disable Secure Boot  via firmware setup. A physically present user must be allowed to disable  Secure Boot via firmware setup without possession of PKpriv. A Windows  Server may also disable Secure Boot remotely using a strongly  authenticated (preferably public-key based) out-of-band management  connection, such as to a baseboard management controller or service  processor. Programmatic disabling of Secure Boot either during Boot  Services or after exiting EFI Boot Services MUST NOT be possible. ** Disabling Secure Boot must not be possible on ARM systems.**

[http://msdn.microsoft.com/en-us/library/windows/hardware/jj128256.aspx](http://msdn.microsoft.com/en-us/library/windows/hardware/jj128256.aspx)



Also I don't know if it is possible to boot the device from usb storage or flash memory.

This is very annoying :@ I have bought the device and I should be allowed run whatever software I wish on it.

---

### Post by Denis63 on 2013-02-26
Yes, you right - its impossible to disable secure boot in ARM devices. But, on the other hand, its possible to boot from flashcard (usb-ctick). You need to press Vol- button and, holding it, turn on the tablet. I did it when recover my system in ASUS Vivo Tab RT from bootable usb-stick with Windows RT (you can create recovery usb-stick in Win RT beforehand). But process of Win RT recovering from flashcard is fully automatical, without any user manipulation (do you remember - secure boot!). So, if we want to install Ubuntu on ASUS VivoTab RT, we should make installation process fully automatical also. Or make it startable right in Win RT (like installation process of ubuntu for x86 can be started in x86 Windows).

---

### Post by vitj on 2013-02-26
> **Denis63 said:**
> So, if we want to install Ubuntu on ASUS VivoTab RT, we should make installation process fully automatical also. Or make it startable right in Win RT (like installation process of ubuntu for x86 can be started in x86 Windows).

So in essence we nead an ARM port of wubi (and whatever else that entails, if feasible). My experience does not lie in this area but as I purchased the device in a foreign country and cannot exchange it for a different model I must seek an alternative as I am not content with running windows.

I am going to seek further input at [http://forum.xda-developers.com/](http://forum.xda-developers.com/) and see if anyone there can provide guidance (or if any members of the community have any input it would be much appreciated :D). I would imagine the hardware to be `fairly similar` to the line of android based transformers sold by asus so don't think there would be any hardware issues with running linux on this device.

Have you tried booting the arm image of ubuntu while holding the -volume button? What was the result of this? I ask because the device was bought from me by a relative (yes after explicitly requesting an android based device:@) and I am yet to take possession of it.  

On the plus side at least software like vim and putty have been ported to arm and can run on a jailbroken windows rt install [http://forum.xda-developers.com/showthread.php?t=2092348](http://forum.xda-developers.com/showthread.php?t=2092348)

---

### Post by Denis63 on 2013-02-27
Glad you're intersted in this topic! About xda conference - I'm registered in this resource. So, what I want to tell - xda is a place for crazy geeks, not for interested everyman like me. Yes, I can jailbrake Win RT in my ASUS Vivo Tab RT, but most part of ported apps is usefull for geeks only (Vim, putty etc). I can create recovery Win RT usb-stick or installable usb stick with Ubuntu. But I can't create UEFI-bootloader emulator to install (to port) Win RT on other ARM-based tablets, like Cotulla did it with HTC. Unfortunatelly, Cotulla didn't give us the solution ((( So, I had a wish, to have ASUS transformer pad Infinity TF700 with ported Win RT, but I still have not... Also with Ububntu for this tablet (TF700) - becose of secure boot, one of the xda members is being creating special distributive of this OS with fully automatical installationn process. Yea, we still can't install ARM version of ubuntu on ARM-based tablets without serious changes in official distributive (((

About my ASUS TF600T - I will try to install tablet version of Ubuntu later, at the moment, when this version become adecuate, without serious glitches ))) Installation of Ubuntu 12.10 for ARM gave me black screen for too long time. I decided, that installation process stopped on the one of non-automatical moments (creating of disk partitions or language choosing or starting options - installation or live cd mode). So, I stopped trying any more.

---

### Post by vitj on 2013-03-10
After reading more into this I now beleive it is impossible unless someone hacks the firmware on the device. The bootloader requires micrsoft private key and I doubt they are willing to give that out.

So annoying, so so annoying. If I had any idea on how to hack the firmware I would but unfotunatly that is not my area of expertise.

---

### Post by vitj on 2013-03-15
I have not tried this yet, as I need to create a restore image first and backup my boot settings. But I am going to try run 
> [INDENT]**bcdedit /set {default} bootmenupolicy standard**
[/INDENT]


from an adminstrator command prompt to see if that will disable secure boot. The reason why is I am curious if microsoft just disabled the menu for disabling secure boot and it is actually possible to disable it. Will report back with findings.

---

### Post by modsbyus on 2013-04-12
> **vitj said:**
> I have not tried this yet, as I need to create a restore image first and backup my boot settings. But I am going to try run 


from an adminstrator command prompt to see if that will disable secure boot. The reason why is I am curious if microsoft just disabled the menu for disabling secure boot and it is actually possible to disable it. Will report back with findings.

Any update on this??

---

### Post by vitj on 2013-04-12
No I am now perfectly happy with windows rt.... 

Hahaha actually no I haven't tried it yet just haven't really had the need to use the device and have been busy with other things. I recommend posting in this thread [http://forum.xda-developers.com/showthread.php?t=2211825](http://forum.xda-developers.com/showthread.php?t=2211825) where people a lot more knowledgable than me are talking about dual booting this device.

---

### Post by vitj on 2013-08-13
There is an exploit for the bootload on the vivotab however the dev who discovered it is keeping it secret [https://twitter.com/Myriachan/status/364314152560377856](https://twitter.com/Myriachan/status/364314152560377856)

---

### Post by vitj on 2014-02-11
Ok so this should now be possible, [http://forum.xda-developers.com/showpost.php?p=50197290&postcount=402](http://forum.xda-developers.com/showpost.php?p=50197290&postcount=402)

I am going to have a play around with this on a jail broken windowsRT 8.0 vivo tab.

---

