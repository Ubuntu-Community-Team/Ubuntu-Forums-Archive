---
title: "What architecture for apt-build on Intel Core2 Duo?"
date: 2007-04-26
forum: Apple Intel Users
---

### Post by SinoDave on 2007-04-26
I'm installing apt-build on my machine running Ubuntu Feisty in a virtual machine via Parallels. I don't know what to choose for the architecture (Pentium4? Prescott? Nocona?). Any help would be greatly appreciated!

SinoDave

---

### Post by ronocdh on 2007-04-27
> **SinoDave said:**
> I'm installing apt-build on my machine running Ubuntu Feisty in a virtual machine via Parallels. I don't know what to choose for the architecture (Pentium4? Prescott? Nocona?). Any help would be greatly appreciated!

SinoDave
"Conroe" I believe was the name. [This]("http://en.wikipedia.org/wiki/Core2_duo#Conroe_2") is all I've found to back me up.

Although I'm sure several people here would defend Parallels, I have heard of some having better luck with VMWare Fusion beta 3. I have downloaded that and given it a spin, and I liked the built-in Ubuntu support, but I've never used Parallels and so can't compare.

Hopefully "Conroe" is an option for you! Post back with results.

---

### Post by midorigin on 2007-04-28
I have the same question. During the installation of apt-build, I'm given the following screen:

> If your architecture is not here, choose one and edit your configuration file (/etc/apt/apt-build.conf) by hand, and please do a wishlist bugreport.

Architecture:
- nocona
- k8
- opteron
- athlon64
- athlon-fx

What choice, if any, is appropriate for an Intel Core 2 Duo?

---

### Post by redfox on 2007-04-28
Those are all AMD chips except for Nocona.  Was there another option somewhere for Intel chips?

Does Parallels emulate the CPU?  I know it emulates a lot of hardware.

---

