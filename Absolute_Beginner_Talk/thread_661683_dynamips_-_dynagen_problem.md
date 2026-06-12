---
title: "dynamips - dynagen problem"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by tasos on 2008-01-08
When i open a .net file with gdynagen or dynagen i get the following error

>  **Dynagen Output :**
Cisco Router Simulation Platform (version 0.2.8-RC2-x86)
Copyright (c) 2005-2007 Christophe Fillot.
Build date: Oct 14 2007 10:41:26

ILT: loaded table "mips64j" from cache.
ILT: loaded table "mips64e" from cache.
ILT: loaded table "ppc32j" from cache.
ILT: loaded table "ppc32e" from cache.
Hypervisor TCP control server started (port 7200).
*** Error: Unknown command 'create'
See dynamips output for more info.

Press ENTER to continue


> 
**Dynamips Output :**
ILT: loaded table "mips64j" from cache.
ILT: loaded table "mips64e" from cache.
ILT: loaded table "ppc32j" from cache.
ILT: loaded table "ppc32e" from cache.
Hypervisor TCP control server started (port 7200).
Shutdown in progress...
Shutdown completed.

Dynamips versions tested : v0.2.7-x86 (Feisty) and v0.2.7-0.2.8RC2 (Gutsy)
Dynagen version tested : v0.9.3.061007 (Feisty)
gDynagen version : v0.1.3-1 (Feisty)
Ubuntu 7.10

Any ideas? Anyone with the same problem?
Thanx

---

### Post by tonyperez on 2008-03-05
> **tasos said:**
> When i open a .net file with gdynagen or dynagen i get the following error





Dynamips versions tested : v0.2.7-x86 (Feisty) and v0.2.7-0.2.8RC2 (Gutsy)
Dynagen version tested : v0.9.3.061007 (Feisty)
gDynagen version : v0.1.3-1 (Feisty)
Ubuntu 7.10

Any ideas? Anyone with the same problem?
Thanx

It looks like there is an invalid line on your net file configuration.

---

