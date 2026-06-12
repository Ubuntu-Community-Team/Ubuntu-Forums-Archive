---
title: "Is there ANY decent distro which handles AMD Graphics?"
date: 2012-06-21
forum: Any Other OS
---

### Post by cyanide911 on 2012-06-21
I have an HP DV6 6121tx, which has integrated Intel graphics, and and AMD Radeon HD6770M. I've tried both Ubuntu and Mint, and both have given me immense problems when trying to make my AMD card work. 
So I have a couple of questions.

1. Is there any decent distro which handles AMD Graphic cards well (INCLUDING GRAPHIC CARD SWITCHING)

2. If not, is there any way to simply NOT involve my AMD card at all and use ONLY my Intel integrated graphics? I'm typing this from my Mint installation and my laptop is getting extremely hot, coupled with pathetic battery life. So I'm assuming it's running/trying to run my AMD card even without proper drivers.

**TL;DR: Want to run any distro on integrated graphics, dont care much about AMD graphics. What do.**

---

### Post by kurt18947 on 2012-06-21
I'm not familiar with models but I believe some laptops have a BIOS settings to disable one of the adapters.  That might be a place to start if you haven't checked yet.

---

### Post by cyanide911 on 2012-06-21
> **kurt18947 said:**
> I'm not familiar with models but I believe some laptops have a BIOS settings to disable one of the adapters.  That might be a place to start if you haven't checked yet.

My laptop has two options in the BIOS. Dynamic and Static switching.

Dynamic being the method in which the system decided between integrated and dedicated on per-application basis.

Static being the method in we have to set which card to use via the Catalyst Control Center.

So both of these require AMD drivers and the CCC to function.

---

### Post by ajgreeny on 2012-06-21
Some amd graphic cards work extremely well with ubuntu and mint, but it will depend on exactly which card you have in the machine.

I've no idea about any switching possibilities with dual card setup of a machine.

---

### Post by UltimateCat on 2012-06-23
> **ajgreeny said:**
> Some amd graphic cards work extremely well with ubuntu and mint, but it will depend on exactly which card you have in the machine.

I've no idea about any switching possibilities with dual card setup of a machine.
I'm running Ubuntu 10.04 ; 2.7 UE and I too had a terrible time with my AMD Radeon graphics card, however; after finding the right driver from the Radeon website compiz has not crashed on me-

Laptops are a bit different and I can't say much because I'm still learning about the new HD graphics and 3rd generation stats.  

Correct me if I am wrong but ( I think) it's not so much the distribution that handles the graphics it's the card it's self and the memory capabilities.

---

### Post by exploder on 2012-06-23
I have an HP DV6 laptop with ATI graphics. The only distro at the moment that the graphics work well on is Fedora 17. I can run Mint and Ubuntu but every once in a while when I boot up I get 9 flickering lojun screens... 

On Mint and Ubuntu the proprietary drivers never finish installing. The multiple logon scrrens happen with the open source drivers. Fedora 17 just works with the open source drivers. 

I have Mint 13 running fine on 3 computers with NVidea graphics but my notebook will have to stay with Fedora until I can figure out the problem with the ATI graphics. PCLinuxOS works perfectly on my notebook but the Falink WiFi is not currently supported.

Give Fedora a try and see what you think.

---

