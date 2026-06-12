---
title: "fglrx removed but still in boot ?"
date: 2005-08-15
forum: Absolute Beginner Talk
---

### Post by Dutch on 2005-08-15
removed fglrx (ati driver)
cannot remove(in Synaptic) :
%%
**Non-free Linux 2.6.10 modules on PPro/Celeron/PII/PIII/PIV**
This package provides restricted modules for Linux version 2.6.10 on
Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV.
Currently the following modules are included:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusba, fcpci,
   fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)
 - ltmodem (Winmodem)
%%

because when I command Synaptic to remove it , Synaptic also want to remove the total Linux-686 packet.

but now I have Error in Boot:
%%
glrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY'** taints kernel**.
[fglrx] Maximum main memory to use for locked dma buffers: 198 MBytes.
[fglrx:firegl_init] *ERROR* Device not found!
[fglrx] Maximum main memory to use for locked dma buffers: 198 MBytes.
[fglrx:firegl_init] *ERROR* Device not found!
[fglrx] Maximum main memory to use for locked dma buffers: 198 MBytes.
[fglrx:firegl_init] *ERROR* Device not found!
[fglrx] Maximum main memory to use for locked dma buffers: 198 MBytes.
[fglrx:firegl_init] *ERROR* Device not found!
%%

In synaptic al the Ati drivers are removed (start up again) but the Error keeps coming.
What now ?

---

### Post by poofyhairguy on 2005-08-16
[QUOTE=Dutch]
What now ?[/QUOTE]

When I switched from an ATI card to a Nvidia one I got the same errors. They seem to be harmless. If they bug you, you can blacklist fglrx.

---

### Post by Dutch on 2005-08-16
[QUOTE=poofyhairguy]When I switched from an ATI card to a Nvidia one I got the same errors. They seem to be harmless. If they bug you, you can blacklist fglrx.[/QUOTE]

How ?

---

