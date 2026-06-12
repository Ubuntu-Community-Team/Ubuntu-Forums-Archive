---
title: "menús desapareguts amb 2 monitors"
date: 2009-02-14
forum: Catalan Team
---

### Post by merril on 2009-02-14
Nota: he posat aquest missatge a un altre post i el moc a un de nou.

> **merril said:**
> 
Al connectar el segon monitor, Ubuntu m'ha demanat que reiniciés, i al tornar a engegar, la barra de menús superior m'ha desaparegut i no puc accedir a cap menú amb el ratolí, bé, només puc accedir al menú de configuració de l'escriptori però no puc canviar la configuració de la pantalla en sí.


Algú em pot dir com puc accedir al terminal o als menús de configuració dels monitors **només amb el teclat**?

El meu equip es un portàtil de l'any de la Quica amb una tarja integrada, però no tinc ni idea de la configuració...:(
Moltes gracies i salutacions.

> **papapep said:**
> 
Hola Merril,

Obre un fil específic pel teu tema, si us plau.

I quan ho facis, ja hi pots enganxar el que et surti en fer:

```
lspci -v
```

al terminal que et sortirà en fer Ctrl+F1 (o Fn, sent n fins a 5), després d'identificar-te, clar.

Salutacions.

Fet Papapep!


----------------------
ordinador@ordinador-vell:~$ **lspci -v**
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
	Subsystem: CLEVO/KAPOK Computer Device 5401
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
	Subsystem: CLEVO/KAPOK Computer Device 5401
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at a0080000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at a0040000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
	Subsystem: CLEVO/KAPOK Computer Device 5401
	Flags: fast devsel
	Memory at 36000000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: <access denied>
-------------------

Únicament enganxo  el referent al processador i a la vcard.
...segueixo sense poder fer res amb això.:confused:

Realment m'he posat a trastejar massa ràpid amb l'Ubuntu; fis i tot havia d'aprendre com engegar un term! :lolflag:

---

